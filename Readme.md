[![Build Status](https://travis-ci.org/SaschaKP/GPX.svg?branch=master)](https://travis-ci.org/SaschaKP/GPX)

GPX was created by Dr. Henry Thomas (aka Wingcommander) in April 2013

GPX is a post processing utility for converting gcode output from 3D slicing software like
Cura, KISSlicer, S3DCreator and Slic3r to x3g files for standalone 3D printing on Makerbot
Cupcake, ThingOMatic, and Replicator 1/2/2x printers - with support for both stock and
sailfish firmwares. My hope is that is little utility will open up Makerbot 3D printers to
a range of new and exciting sources and utilities for 3D printing input.

This release and source in particular is focused to be used with simplify3D, a program distributed on https://www.simplify3d.com/

The reason that got me on the modifications is to allow other users as well to remove certain software limits, and allow for the true makers, to adjust missing functionality.

Usage:

gpx [-dgiprsuvw] [-b B] [-c C] [-f F] [-m M] [-x X] [-y Y] [-z Z] IN [OUT]

Options:

	-d	simulated ditto printing
	-g	Makerbot/ReplicatorG GCODE flavor
	-i	enable stdin and stdout support for command line pipes
	-p	override build percentage
	-r	Reprap GCODE flavor
	-s	enable USB serial I/O and send x3G output to 3D printer (only on non-windows systems)
	-u  Custom Machine Settings
	-v	verbose mode
	-w	rewrite 5d extrusion values

B is baudrate for serial I/O (default is 115200 - only on non-windows systems)

C is the filename of a custom machine definition (ini)

F is the actual filament diameter in the printer

M is the predefined machine type:

	c3  = Cupcake Gen3 XYZ, Mk5/6 + Gen4 Extruder
	c4  = Cupcake Gen4 XYZ, Mk5/6 + Gen4 Extruder
	cp4 = Cupcake Pololu XYZ, Mk5/6 + Gen4 Extruder
	cpp = Cupcake Pololu XYZ, Mk5/6 + Pololu Extruder
	t6  = TOM Mk6 - single extruder
	t7  = TOM Mk7 - single extruder
	t7d = TOM Mk7 - dual extruder
	r1  = Replicator 1 - single extruder
	r1d = Replicator 1 - dual extruder
	r2  = Replicator 2 (default)
	r2h = Replicator 2 with HBP
	r2x = Replicator 2X
	m180 = Maylan M180
	3dimulti = 3Dison Multi
	3dipro = 3Dison Pro
	3dih700 = 3Dison H700
	cxy = Core-XY with HBP - single extruder
	cxysz = Core-XY with HBP - single extruder, slow z
	zyyx = ZYYX 3D printer, single extruder
	zyyxdual = ZYYX 3D printer, dual extruder
	zyyxpro = ZYYX 3D printer, Pro Version

X,Y & Z are the coordinate system offsets for the conversion:

	X = the x axis offset
	Y = the y axis offset
	Z = the z axis offset

IN is the name of the sliced gcode input filename

OUT is the name of the x3g output filename or the serial I/O port

Examples:

	gpx -p -m r2 my-sliced-model.gcode
	gpx -c custom-tom.ini example.gcode /volumes/things/example.x3g
	gpx -x 3 -y -3 offset-model.gcode
	gpx -m c4 -s sio-example.gcode /dev/tty.usbmodem


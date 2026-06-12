---
title: "Wacom notworking with Maya"
date: 2009-02-04
forum: Art &amp; Design
---

### Post by FrostBlue on 2009-02-04
Ok this just started recently after a few upgrade on Hardy.
I used to use wacom bamboo for painting in Maya regularly.Now after a bunch of updates Maya crashes on most painting operations (Sculp tool,Weight painting,etc).
At first I thought it was a grphics problem,so I fiddled with xorg.conf file.But guess what,this weird Maya behaviour stops if I remove some lines from xorg.conf which help the wacom tablet,I have pasted the lines below,

[COLOR="Navy"]Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
#InputDevice    "stylus"    "SendCoreEvents"
#InputDevice    "eraser"    "SendCoreEvents"
#InputDevice    "cursor"    "SendCoreEvents"
#InputDevice    "pad"
EndSection[/COLOR]

The lines commented out seem to be messing Maya paint tools.

Anybody has any idea whats going on? I want to use both bamboo and Maya together.

Much appreciated.

---

### Post by skullmunky on 2009-08-04
Hey, did you ever get this working?  I've had trouble with this in the past, but am now using my Intuos3 with Maya 2009 on Jaunty and it seems a lot more stable.

Whoops, spoke too soon.  here's a stack trace from maya freezing horribly while paint-weighting.  Anyone able to decipher it?

```

GNU gdb 6.8-debian                                                                         
Copyright (C) 2008 Free Software Foundation, Inc.                                          
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>              
This is free software: you are free to change and redistribute it.                         
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"                 
and "show warranty" for details.                                                           
This GDB was configured as "x86_64-linux-gnu"...                                           
(no debugging symbols found)                                                               
(gdb) r                                                                                    
Starting program: /usr/autodesk/maya2009-x64/bin/maya.bin                                  
[Thread debugging using libthread_db enabled]                                              
[New Thread 0x7f0665f5f790 (LWP 21971)]                                                    
[New Thread 0x7f0656259950 (LWP 21990)]                                                    
[New Thread 0x7f0655e58950 (LWP 21991)]                                                    
MAYA_DEBUG_NO_SIGNAL_HANDLERS is set.                                                      

[New Thread 0x7f064e39b950 (LWP 22033)]
mental ray for Maya 10.0               
[New Thread 0x7f0648f88950 (LWP 22041)]
[New Thread 0x7f0648d87950 (LWP 22042)]
mental ray: version 3.7.1.26, Jul 30 2008, revision 26576
[New Thread 0x7f0655643950 (LWP 22211)]
[New Thread 0x7f0646071950 (LWP 22212)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f0665f5f790 (LWP 21971)]
0x00007f065aaed6ed in malloc_consolidate (av=0x7f065ade2a00) at malloc.c:4905
4905    malloc.c: No such file or directory.
        in malloc.c
(gdb) bt
#0  0x00007f065aaed6ed in malloc_consolidate (av=0x7f065ade2a00) at malloc.c:4905
#1  0x00007f065aaef8f1 in _int_malloc (av=0x7f065ade2a00, bytes=0) at malloc.c:4229
#2  0x00007f065aaf1828 in *__GI___libc_malloc (bytes=8000) at malloc.c:3551
#3  0x00007f065cd52197 in ?? () from /usr/lib/libGL.so.1
#4  0x00007f0656fe6b0d in ?? () from /usr/lib/tls/libnvidia-tls.so.1
#5  0x00007f066338ea18 in Tarray::allocateArray () from /usr/autodesk/maya2009-x64/lib/libFoundation.so
#6  0x00007f066338e89f in Tarray::expandArray () from /usr/autodesk/maya2009-x64/lib/libFoundation.so
#7  0x00007f066338e5ec in Tarray::changeLogicalSizeTo () from /usr/autodesk/maya2009-x64/lib/libFoundation.so
#8  0x00007f066339d14d in TspatialGrid::TspatialGrid () from /usr/autodesk/maya2009-x64/lib/libFoundation.so
#9  0x00007f066133175d in _ZN14TpolyVoxelGridC9ERK15TfltBoundingBoxRK7T3Int32RK9TpolyGeom () from /usr/autodesk/maya2009-x64/lib/libPolyEngine.so
#10 0x00007f0661331720 in TpolyVoxelGrid::TpolyVoxelGrid () from /usr/autodesk/maya2009-x64/lib/libPolyEngine.so
#11 0x00007f0661330f9a in _ZN23TpolySpatialSubdivisionC9ERK9TpolyGeomRK21TmeshIsectAccelParams () from /usr/autodesk/maya2009-x64/lib/libPolyEngine.so
#12 0x00007f0661331b9c in TpolySpatialSubdivision::TpolySpatialSubdivision () from /usr/autodesk/maya2009-x64/lib/libPolyEngine.so
#13 0x00007f0661392015 in TpolyGeom::getIntersectionAccelerator () from /usr/autodesk/maya2009-x64/lib/libPolyEngine.so
#14 0x00007f06601366bd in TartPolyGeometry::validPolyGeom () from /usr/autodesk/maya2009-x64/lib/libPoly.so
#15 0x00007f06510e1be0 in TartAttrContext::finalize () from /usr/autodesk/maya2009-x64/lib/libJasperSlice.so
#16 0x00007f065f133142 in TselectContext::doRelease () from /usr/autodesk/maya2009-x64/lib/libSharedUI.so
#17 0x00007f06510f38c6 in TartBaseContext::doRelease () from /usr/autodesk/maya2009-x64/lib/libJasperSlice.so
#18 0x00007f06510e22a6 in TartAttrContext::doRelease () from /usr/autodesk/maya2009-x64/lib/libJasperSlice.so
#19 0x00007f06620f8012 in TtoolContext::preDoRelease () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#20 0x00007f065f140af1 in TstandardContext::preDoRelease () from /usr/autodesk/maya2009-x64/lib/libSharedUI.so
#21 0x00007f06620f68c7 in TtoolCallback::doIt () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#22 0x00007f06620a3ef2 in Tcontrol::doRelease () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#23 0x00007f066201e535 in Tresponder::handleEvent () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#24 0x00007f06620a3cc7 in Tcontrol::xEventHandler () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#25 0x00007f065c0f02ee in XtDispatchEventToWidget () from /usr/lib/libXt.so.6
#26 0x00007f065c0f0b1f in ?? () from /usr/lib/libXt.so.6
#27 0x00007f065c0efa31 in XtDispatchEvent () from /usr/lib/libXt.so.6
#28 0x00007f066201b3e9 in TeventHandler::analyzeEvent () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#29 0x00007f066201b548 in TeventHandler::processXEvent () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#30 0x00007f066201b5e4 in TunixEventHandler::handleEvents () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#31 0x00007f0662010457 in Tapplication::start () from /usr/autodesk/maya2009-x64/lib/libExtensionLayer.so
#32 0x000000000041060b in appmain ()
#33 0x000000000041e93b in main ()

```

---


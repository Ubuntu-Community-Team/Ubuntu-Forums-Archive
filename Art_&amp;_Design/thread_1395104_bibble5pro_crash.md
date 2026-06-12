---
title: "bibble5pro crash"
date: 2010-01-31
forum: Art &amp; Design
---

### Post by earlycj5 on 2010-01-31
Hey all, I'm trying out LightZone and bibble5pro right now to compare them with my current workflow and results using F-Spot -> UFRAW Gimp Plugin -> Gimp.

LightZone installed fine.  I need to spend more time with it and learn how to effectively use it.

bibble5pro OTOH won't launch at all.  I downloaded and installed the .deb and have ia32libs installed as per the requirements.

I'm getting this when I try to launch:
```

Install Path:           /opt/bibble5pro
LD_PATH:                /opt/bibble5pro/lib:
XLIB_SKIP_ARGB_VISUALS: 1
	linux-gate.so.1 =>  (0xf7f68000)
	libkodakcms.so => /opt/bibble5pro/lib/libkodakcms.so (0xf7eec000)
	libuuid.so.1 => /opt/bibble5pro/lib/libuuid.so.1 (0x0070c000)
	libtcmalloc_minimal.so.0 => /opt/bibble5pro/lib/libtcmalloc_minimal.so.0 (0xf7eb9000)
	libQtSvg.so.4 => /opt/bibble5pro/lib/libQtSvg.so.4 (0xf7e6d000)
	libQt3Support.so.4 => /opt/bibble5pro/lib/libQt3Support.so.4 (0xf7b88000)
	libQtSql.so.4 => /opt/bibble5pro/lib/libQtSql.so.4 (0xf7aef000)
	libQtOpenGL.so.4 => /opt/bibble5pro/lib/libQtOpenGL.so.4 (0xf7a79000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf79e7000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf792d000)
	libQtNetwork.so.4 => /opt/bibble5pro/lib/libQtNetwork.so.4 (0xf7831000)
	libQtDesigner.so.4 => /opt/bibble5pro/lib/libQtDesigner.so.4 (0xf7555000)
	libQtScript.so.4 => /opt/bibble5pro/lib/libQtScript.so.4 (0xf7433000)
	libQtXml.so.4 => /opt/bibble5pro/lib/libQtXml.so.4 (0xf73ee000)
	libQtGui.so.4 => /opt/bibble5pro/lib/libQtGui.so.4 (0xf6b06000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6ae0000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6ad7000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6abe000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6ab4000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6aaa000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6aa2000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6a2b000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf69fd000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf69ed000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf68fe000)
	libQtCore.so.4 => /opt/bibble5pro/lib/libQtCore.so.4 (0xf66d9000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf66c3000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf66bd000)
	librt.so.1 => /lib32/librt.so.1 (0xf66b3000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf65fb000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf65f7000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf65de000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf64ef000)
	libm.so.6 => /lib32/libm.so.6 (0xf64c9000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf64b9000)
	libc.so.6 => /lib32/libc.so.6 (0xf6356000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf543e000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf543c000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf5414000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf5410000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf53f6000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf53c4000)
	/lib/ld-linux.so.2 (0xf7f69000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf53be000)
*** glibc detected *** ./bibblepro: free(): invalid pointer: 0x0989c000 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf640f204]
/lib32/libc.so.6(cfree+0x96)[0xf64111e6]
/usr/lib32/tls/libnvidia-tls.so.1[0xf5485aa0]
======= Memory map: ========
0070c000-0070f000 r-xp 00000000 08:02 196455                             /opt/bibble5pro/lib/libuuid.so
0070f000-00710000 rwxp 00002000 08:02 196455                             /opt/bibble5pro/lib/libuuid.so
08048000-09070000 r-xp 00000000 08:02 196242                             /opt/bibble5pro/bin/bibblepro
09070000-0908a000 rwxp 01028000 08:02 196242                             /opt/bibble5pro/bin/bibblepro
0908a000-090af000 rwxp 0908a000 00:00 0 
09800000-099a0000 rwxp 09800000 00:00 0                                  [heap]
f5405000-f5407000 rwxp f5405000 00:00 0 
f5407000-f540b000 r-xp 00000000 08:02 484815                             /usr/lib32/libXdmcp.so.6.0.0
f540b000-f540c000 rwxp 00003000 08:02 484815                             /usr/lib32/libXdmcp.so.6.0.0
f540c000-f540d000 rwxp f540c000 00:00 0 
f540d000-f543d000 r-xp 00000000 08:02 16456                              /lib32/libpcre.so.3.12.1
f543d000-f543e000 r-xp 0002f000 08:02 16456                              /lib32/libpcre.so.3.12.1
f543e000-f543f000 rwxp 00030000 08:02 16456                              /lib32/libpcre.so.3.12.1
f543f000-f5457000 r-xp 00000000 08:02 484811                             /usr/lib32/libxcb.so.1.1.0
f5457000-f5458000 r-xp 00017000 08:02 484811                             /usr/lib32/libxcb.so.1.1.0
f5458000-f5459000 rwxp 00018000 08:02 484811                             /usr/lib32/libxcb.so.1.1.0
f5459000-f545b000 r-xp 00000000 08:02 484807                             /usr/lib32/libXau.so.6.0.0
f545b000-f545c000 r-xp 00001000 08:02 484807                             /usr/lib32/libXau.so.6.0.0
f545c000-f545d000 rwxp 00002000 08:02 484807                             /usr/lib32/libXau.so.6.0.0
f545d000-f5481000 r-xp 00000000 08:02 484690                             /usr/lib32/libexpat.so.1.5.2
f5481000-f5483000 r-xp 00023000 08:02 484690                             /usr/lib32/libexpat.so.1.5.2
f5483000-f5484000 rwxp 00025000 08:02 484690                             /usr/lib32/libexpat.so.1.5.2
f5484000-f5485000 rwxp f5484000 00:00 0 
f5485000-f5486000 r-xp 00000000 08:02 524036                             /usr/lib32/tls/libnvidia-tls.so.180.44
f5486000-f5487000 rwxp 00000000 08:02 524036                             /usr/lib32/tls/libnvidia-tls.so.180.44
f5487000-f61a1000 r-xp 00000000 08:02 484136                             /usr/lib32/libGLcore.so.180.44
f61a1000-f6393000 rwxp 00d19000 08:02 484136                             /usr/lib32/libGLcore.so.180.44
f6393000-f639f000 rwxp f6393000 00:00 0 
f639f000-f64fb000 r-xp 00000000 08:02 16368                              /lib32/libc-2.9.so
f64fb000-f64fc000 ---p 0015c000 08:02 16368                              /lib32/libc-2.9.so
f64fc000-f64fe000 r-xp 0015c000 08:02 16368                              /lib32/libc-2.9.so
f64fe000-f64ff000 rwxp 0015e000 08:02 16368                              /lib32/libc-2.9.so
f64ff000-f6502000 rwxp f64ff000 00:00 0 
f6502000-f650f000 r-xp 00000000 08:02 484641                             /usr/lib32/libgcc_s.so.1
f650f000-f6510000 r-xp 0000c000 08:02 484641                             /usr/lib32/libgcc_s.so.1
f6510000-f6511000 rwxp 0000d000 08:02 484641                             /usr/lib32/libgcc_s.so.1
f6511000-f6512000 rwxp f6511000 00:00 0 
f6512000-f6536000 r-xp 00000000 08:02 16372                              /lib32/libm-2.9.so
f6536000-f6537000 r-xp 00023000 08:02 16372                              /lib32/libm-2.9.so
f6537000-f6538000 rwxp 00024000 08:02 16372                              /lib32/libm-2.9.so
f6538000-f661c000 r-xp 00000000 08:02 484644                             /usr/lib32/libstdc++.so.6.0.10
f661c000-f6620000 r-xp 000e3000 08:02 484644                             /usr/lib32/libstdc++.so.6.0.10
f6620000-f6621000 rwxp 000e7000 08:02 484644                             /usr/lib32/libstdc++.so.6.0.10
f6621000-f6627000 rwxp f6621000 00:00 0 
f6627000-f663c000 r-xp 00000000 08:02 16393                              /lib32/libpthread-2.9.so
f663c000-f663d000 r-xp 00014000 08:02 16393                              /lib32/libpthread-2.9.so
f663d000-f663e000 rwxp 00015000 08:02 16393                              /lib32/libpthread-2.9.so
f663e000-f6640000 rwxp f663e000 00:00 0 
f6640000-f6642000 r-xp 00000000 08:02 16371                              /lib32/libdl-2.9.so
f6642000-f6643000 r-xp 00001000 08:02 16371                              /lib32/libdl-2.9.so
f6643000-f6644000 rwxp 00002000 08:02 16371                              /lib32/libdl-2.9.so
f6644000-f66fa000 r-xp 00000000 08:02 484705                             /usr/lib32/libglib-2.0.so.0.2000.1
f66fa000-f66fb000 r-xp 000b5000 08:02 484705                             /usr/lib32/libglib-2.0.so.0.2000.1
f66fb000-f66fc000 rwxp 000b6000 08:02 484705                             /usr/lib32/libglib-2.0.so.0.2000.1
f66fc000-f6703000 r-xp 00000000 08:02 16408                              /lib32/librt-2.9.so
f6703000-f6704000 r-xp 00006000 08:02 16408                              /lib32/librt-2.9.so
f6704000-f6705000 rwxp 00007000 08:02 16408                              /lib32/librt-2.9.so
f6705000-f6706000 rwxp f6705000 00:00 0 
f6706000-f670a000 r-xp 00000000 08:02 484708                             /usr/lib32/libgthread-2.0.so.0.2000.1
f670a000-f670b000 r-xp 00003000 08:02 484708                             /usr/lib32/libgthread-2.0.so.0.2000.1
f670b000-f670c000 rwxp 00004000 08:02 484708                             /usr/lib32/libgthread-2.0.so.0.2000.1
f670c000-f6720000 r-xp 00000000 08:02 484642                             /usr/lib32/libz.so.1.2.3.3
f6720000-f6721000 r-xp 00013000 08:02 484642                             /usr/lib32/libz.so.1.2.3.3
f6721000-f6722000 rwxp 00014000 08:02 484642                             /usr/lib32/libz.so.1.2.3.3
f6722000-f693f000 r-xp 00000000 08:02 196456                             /opt/bibble5pro/lib/libQtCore.so.4
f693f000-f6946000 rwxp 0021d000 08:02 196456                             /opt/bibble5pro/lib/libQtCore.so.4
f6946000-f6947000 rwxp f6946000 00:00 0 
f6947000-f6a31000 r-xp 00000000 08:02 484806                             /usr/lib32/libX11.so.6.2.0
f6a31000-f6a32000 ---p 000ea000 08:02 484806                             /usr/lib32/libX11.so.6.2.0
f6a32000-f6a33000 r-xp 000ea000 08:02 484806                             /usr/lib32/libX11.so.6.2.0
f6a33000-f6a35000 rwxp 000eb000 08:02 484806                             /usr/lib32/libX11.so.6.2.0
f6a35000-f6a36000 rwxp f6a35000 00:00 0 
f6a36000-f6a44000 r-xp 00000000 08:02 484816                             /usr/lib32/libXext.so.6.4.0
f6a44000-f6a45000 r-xp 0000d000 08:02 484816                             /usr/lib32/libXext.so.6.4.0
f6a45000-f6a46000 rwxp 0000e000 08:02 484816                             /usr/lib32/libXext.so.6.4.0
f6a46000-f6a71000 r-xp 00000000 08:02 484697                             /usr/lib32/libfontconfig.so.1.3.0
f6a71000-f6a72000 r-xp 0002a000 08:02 484697                             /usr/lib32/libfontconfig.so.1.3.0
f6a72000-f6a73000 rwxp 0002b000 08:02 484697                             /usr/lib32/libfontconfig.so.1.3.0
f6a73000-f6a74000 rwxp f6a73000 00:00 0 
f6a74000-f6ae6000 r-xp 00000000 08:02 484698                             /usr/lib32/libfreetype.so.6.3.20
f6ae6000-f6aea000 r-xp 00071000 08:02 484698                             /usr/lib32/libfreetype.so.6.3.20
f6aea000-f6aeb000 rwxp 00075000 08:02 484698                             /usr/lib32/libfreetype.so.6.3.20
f6aeb000-f6af1000 r-xp 00000000 08:02 484826                             /usr/lib32/libXrandr.so.2.2.0
f6af1000-f6af2000 r-xp 00006000 08:02 484826                             /usr/lib32/libXrandr.so.2.2.0
f6af2000-f6af3000 rwxp 00007000 08:02 484826                             /usr/lib32/libXrandr.so.2.2.0
f6af3000-f6afb000 r-xp 00000000 08:02 484827                             /usr/lib32/libXrender.so.1.3.0
f6afb000-f6afc000 r-xp 00007000 08:02 484827                             /usr/lib32/libXrender.so.1.3.0
f6afc000-f6afd000 rwxp 00008000 08:02 484827                             /usr/lib32/libXrender.so.1.3.0
f6afd000-f6b05000 r-xp 00000000 08:02 484819   Aborted

```

Any suggestions?

I'm using Ubuntu Studio Jaunty x64.

---

### Post by garryknight on 2010-01-31
No idea what's causing your problem, but you might like to ask on the Bibble forums where the staff regularly answer this kind of problem.
[http://support.bibblelabs.com/webboard/index.php](http://support.bibblelabs.com/webboard/index.php)

---

### Post by earlycj5 on 2010-02-01
> **garryknight said:**
> No idea what's causing your problem, but you might like to ask on the Bibble forums where the staff regularly answer this kind of problem.
[http://support.bibblelabs.com/webboard/index.php](http://support.bibblelabs.com/webboard/index.php)

Thanks.

---


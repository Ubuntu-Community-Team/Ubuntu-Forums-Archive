---
title: "Need help installing ARToolkit (.tgz)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by jtreach on 2007-01-21
I've just migrated to Ubuntu from windows xp (although I'm still dual booting in order to use my Zune) I am trying to get my eyetoy working on ubuntu and a little googling later and it turns out that this program ARTool kit can help me. 

I downloaded the .tgz file from [http://sourceforge.net/projects/artoolkit](http://sourceforge.net/projects/artoolkit)

I then extracted it.... and well then I'm stuck... I've tried running a file named 'configure' a couple of times though it doesn't seem to do anything.... can you help?! I'm a complete n00b and have been running ubuntu for about 8 hours now.

](*,)

---

### Post by zerhacke on 2007-01-21
First install the package "build-essential" from the repositories.  In a terminal, type

```
sudo apt-get install build-essential
```

And hit enter. Supply your own password and hit enter again.  Alternatively, if you don't want to muck around in a command prompt, you can use Synaptic in System - Administration - Synaptic Package Manager.

After you have it installed, then you can run the following commands to configure, compile, then install your software.

In a terminal, type

```
./configure
make
sudo make install
```

---

### Post by jtreach on 2007-01-21
I have installed the build essential package.

When you say open terminal and type:

 ./configure
make
sudo make install

Do you mean configure as in the file that i downloaded (the one i mentioned in my first post) or something completely different and by writing those commands on different lines am i meant to execute each one seperately or all together?

Thanks for your help btw

---

### Post by zerhacke on 2007-01-21
Issue each command on a separate line one at a time.  First issue

```
./configure
```

(make sure you put the dot slash before configure.)

When that is done, issue

```
make
```

When that is done, issue

```
sudo make install
```

---

### Post by jtreach on 2007-01-21
When i execute ./configure terminal just comes up with 

josh@Uber-Computer:~$ ./configure
bash: ./configure: No such file or directory

?

(and yes i did name my computer uber-computer)

---

### Post by zerhacke on 2007-01-21
> **jtreach said:**
> When i execute ./configure terminal just comes up with 

josh@Uber-Computer:~$ ./configure
bash: ./configure: No such file or directory

Make sure you're in the directory you extracted the files to.  It looks to me like you're in the home folder, and your software is probably extracted to a folder within the home folder.  Use "cd whatever-folder-name" without the quotes in a terminal to get to the folder your software is extracted to.

> (and yes i did name my computer uber-computer)

Hahahha!:p

---

### Post by taurus on 2007-01-21
Post output of this.

```
ls -la ~/Desktop
```

Look at Section 4.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jtreach on 2007-01-21
Okay almost there, i managed to do everything you said.

When i got to 'sudo make install' it said "No rule to make target `install'. Stop."

When i executed "make" i noticed this make[2]: Leaving directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/Gl'
make[1]: *** [all] Error 2

---

### Post by jtreach on 2007-01-21
Okay I tried going from the original .tgz using the tutorial suggested by Taurus.

This was the entire command line output for everything passed "tar -xvzf ARToolKit.tgz"

```

josh@Uber-Computer:/tmp$ cd ARToolKit
josh@Uber-Computer:/tmp/ARToolKit$ ./configure
bash: ./configure: No such file or directory
josh@Uber-Computer:/tmp/ARToolKit$ ./Configure
Select a video capture driver.
  1: Video4Linux
  2: Video4Linux+JPEG Decompression (EyeToy)
  3: Digital Video Camcoder through IEEE 1394 (DV Format)
  4: Digital Video Camera through IEEE 1394 (VGA NONCOMPRESSED Image Format)
  5: GStreamer Media Framework
Enter : 2
Do you want to create debug symbols? (y or n)
Enter : n
Build gsub libraries with texture rectangle support? (y or n)
GL_NV_texture_rectangle is supported on most NVidia graphics cards
and on ATi Radeon and better graphics cards
Enter : y
  create ./Makefile
  create lib/SRC/Makefile
  create lib/SRC/AR/Makefile
  create lib/SRC/ARMulti/Makefile
  create lib/SRC/Gl/Makefile
  create lib/SRC/VideoLinux1394Cam/Makefile
  create lib/SRC/VideoLinuxDV/Makefile
  create lib/SRC/VideoLinuxV4L/Makefile
  create lib/SRC/VideoSGI/Makefile
  create lib/SRC/VideoMacOSX/Makefile
  create lib/SRC/VideoGStreamer/Makefile
  create lib/SRC/ARvrml/Makefile
  create util/Makefile
  create util/calib_camera2/Makefile
  create util/calib_cparam/Makefile
  create util/calib_distortion/Makefile
  create util/mk_patt/Makefile
  create util/graphicsTest/Makefile
  create util/videoTest/Makefile
  create examples/Makefile
  create examples/collide/Makefile
  create examples/exview/Makefile
  create examples/loadMultiple/Makefile
  create examples/modeTest/Makefile
  create examples/multi/Makefile
  create examples/optical/Makefile
  create examples/paddle/Makefile
  create examples/paddleDemo/Makefile
  create examples/paddleInteraction/Makefile
  create examples/range/Makefile
  create examples/relation/Makefile
  create examples/simple/Makefile
  create examples/simple2/Makefile
  create examples/simpleLite/Makefile
  create examples/twoView/Makefile
  create examples/simpleVRML/Makefile
  create include/AR/config.h
Done.
josh@Uber-Computer:/tmp/ARToolKit$ make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/tmp/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/tmp/ARToolKit/lib/SRC/AR'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAlloc.c
ar rs ../../libAR.a mAlloc.o
ar: creating ../../libAR.a
rm -f mAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mFree.c
ar rs ../../libAR.a mFree.o
rm -f mFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocDup.c
ar rs ../../libAR.a mAllocDup.o
rm -f mAllocDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDup.c
ar rs ../../libAR.a mDup.o
rm -f mDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocTrans.c
ar rs ../../libAR.a mAllocTrans.o
rm -f mAllocTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mTrans.c
ar rs ../../libAR.a mTrans.o
rm -f mTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocMul.c
ar rs ../../libAR.a mAllocMul.o
rm -f mAllocMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mMul.c
ar rs ../../libAR.a mMul.o
rm -f mMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocInv.c
ar rs ../../libAR.a mAllocInv.o
rm -f mAllocInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mInv.c
ar rs ../../libAR.a mInv.o
rm -f mInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mSelfInv.c
ar rs ../../libAR.a mSelfInv.o
rm -f mSelfInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocUnit.c
ar rs ../../libAR.a mAllocUnit.o
rm -f mAllocUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mUnit.c
ar rs ../../libAR.a mUnit.o
rm -f mUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDisp.c
ar rs ../../libAR.a mDisp.o
rm -f mDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDet.c
ar rs ../../libAR.a mDet.o
rm -f mDet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mPCA.c
ar rs ../../libAR.a mPCA.o
rm -f mPCA.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vAlloc.c
ar rs ../../libAR.a vAlloc.o
rm -f vAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vDisp.c
ar rs ../../libAR.a vDisp.o
rm -f vDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vFree.c
ar rs ../../libAR.a vFree.o
rm -f vFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vHouse.c
ar rs ../../libAR.a vHouse.o
rm -f vHouse.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vInnerP.c
ar rs ../../libAR.a vInnerP.o
rm -f vInnerP.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vTridiag.c
ar rs ../../libAR.a vTridiag.o
rm -f vTridiag.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramGet.c
ar rs ../../libAR.a paramGet.o
rm -f paramGet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDecomp.c
ar rs ../../libAR.a paramDecomp.o
rm -f paramDecomp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDistortion.c
ar rs ../../libAR.a paramDistortion.o
rm -f paramDistortion.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramChangeSize.c
ar rs ../../libAR.a paramChangeSize.o
rm -f paramChangeSize.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramFile.c
ar rs ../../libAR.a paramFile.o
rm -f paramFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDisp.c
ar rs ../../libAR.a paramDisp.o
rm -f paramDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker.c
ar rs ../../libAR.a arDetectMarker.o
rm -f arDetectMarker.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat.c
ar rs ../../libAR.a arGetTransMat.o
rm -f arGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat2.c
ar rs ../../libAR.a arGetTransMat2.o
rm -f arGetTransMat2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat3.c
ar rs ../../libAR.a arGetTransMat3.o
rm -f arGetTransMat3.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMatCont.c
ar rs ../../libAR.a arGetTransMatCont.o
rm -f arGetTransMatCont.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arLabeling.c
ar rs ../../libAR.a arLabeling.o
rm -f arLabeling.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker2.c
ar rs ../../libAR.a arDetectMarker2.o
rm -f arDetectMarker2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetMarkerInfo.c
ar rs ../../libAR.a arGetMarkerInfo.o
rm -f arGetMarkerInfo.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetCode.c
ar rs ../../libAR.a arGetCode.o
rm -f arGetCode.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arUtil.c
arUtil.c: In function ‘arGetVersion’:
arUtil.c:46: warning: incompatible implicit declaration of built-in function ‘exit’
ar rs ../../libAR.a arUtil.o
rm -f arUtil.o
make[2]: Leaving directory `/tmp/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/tmp/ARToolKit/lib/SRC/ARMulti'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiReadConfigFile.c
ar rs ../../libARMulti.a arMultiReadConfigFile.o
ar: creating ../../libARMulti.a
rm -f arMultiReadConfigFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiGetTransMat.c
ar rs ../../libARMulti.a arMultiGetTransMat.o
rm -f arMultiGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiActivate.c
ar rs ../../libARMulti.a arMultiActivate.o
rm -f arMultiActivate.o
make[2]: Leaving directory `/tmp/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/tmp/ARToolKit/lib/SRC/Gl'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include gsub.c
gsub.c:8:23: error: GL/glut.h: No such file or directory
gsub.c:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glid’
gsub.c:91: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘maxRectangleTextureSize’
gsub.c: In function ‘argInit2’:
gsub.c:160: error: ‘GLUT_DOUBLE’ undeclared (first use in this function)
gsub.c:160: error: (Each undeclared identifier is reported only once
gsub.c:160: error: for each function it appears in.)
gsub.c:160: error: ‘GLUT_RGBA’ undeclared (first use in this function)
gsub.c:160: error: ‘GLUT_DEPTH’ undeclared (first use in this function)
gsub.c:160: error: ‘GLUT_STENCIL’ undeclared (first use in this function)
gsub.c:166: error: ‘GLUT_SCREEN_WIDTH’ undeclared (first use in this function)
gsub.c:167: error: ‘GLUT_SCREEN_HEIGHT’ undeclared (first use in this function)
gsub.c:189: error: ‘glid’ undeclared (first use in this function)
gsub.c:190: error: ‘GL_TEXTURE_2D’ undeclared (first use in this function)
gsub.c:191: error: ‘GL_UNPACK_ALIGNMENT’ undeclared (first use in this function)
gsub.c:192: error: ‘GL_TEXTURE_WRAP_S’ undeclared (first use in this function)
gsub.c:192: error: ‘GL_CLAMP’ undeclared (first use in this function)
gsub.c:193: error: ‘GL_TEXTURE_WRAP_T’ undeclared (first use in this function)
gsub.c:194: error: ‘GL_TEXTURE_MAG_FILTER’ undeclared (first use in this function)
gsub.c:194: error: ‘GL_NEAREST’ undeclared (first use in this function)
gsub.c:195: error: ‘GL_TEXTURE_MIN_FILTER’ undeclared (first use in this function)
gsub.c:196: error: ‘GL_TEXTURE_ENV’ undeclared (first use in this function)
gsub.c:196: error: ‘GL_TEXTURE_ENV_MODE’ undeclared (first use in this function)
gsub.c:196: error: ‘GL_DECAL’ undeclared (first use in this function)
gsub.c: In function ‘argInitLoop’:
gsub.c:261: error: ‘GL_COLOR_BUFFER_BIT’ undeclared (first use in this function)
gsub.c: In function ‘argDrawMode2D’:
gsub.c:280: error: ‘GL_MODELVIEW’ undeclared (first use in this function)
gsub.c:282: error: ‘GL_PROJECTION’ undeclared (first use in this function)
gsub.c: In function ‘argDrawMode3D’:
gsub.c:306: error: ‘GL_MODELVIEW’ undeclared (first use in this function)
gsub.c: In function ‘argDraw3dLeft’:
gsub.c:316: error: ‘GL_PROJECTION’ undeclared (first use in this function)
gsub.c: In function ‘argDraw3dRight’:
gsub.c:326: error: ‘GL_PROJECTION’ undeclared (first use in this function)
gsub.c: In function ‘argDraw3dCamera’:
gsub.c:344: error: ‘GL_PROJECTION’ undeclared (first use in this function)
gsub.c: In function ‘argDispImage’:
gsub.c:377: error: ‘GL_SCISSOR_TEST’ undeclared (first use in this function)
gsub.c:380: error: ‘maxRectangleTextureSize’ undeclared (first use in this function)
gsub.c: In function ‘argDispImageDrawPixels’:
gsub.c:400: error: ‘GLfloat’ undeclared (first use in this function)
gsub.c:400: error: expected ‘;’ before ‘zoom’
gsub.c:403: error: ‘zoom’ undeclared (first use in this function)
gsub.c:417: error: ‘GL_TEXTURE_2D’ undeclared (first use in this function)
gsub.c:436: error: ‘GL_RGB_EXT’ undeclared (first use in this function)
gsub.c:436: error: ‘GL_UNSIGNED_BYTE’ undeclared (first use in this function)
gsub.c: In function ‘argDispImageTex4’:
gsub.c:692: error: ‘GL_TEXTURE_2D’ undeclared (first use in this function)
gsub.c:693: error: ‘GL_TEXTURE’ undeclared (first use in this function)
gsub.c:695: error: ‘GL_MODELVIEW’ undeclared (first use in this function)
gsub.c:697: error: ‘glid’ undeclared (first use in this function)
gsub.c:702: error: ‘GL_UNPACK_ROW_LENGTH’ undeclared (first use in this function)
gsub.c:720: error: ‘GL_RGB_EXT’ undeclared (first use in this function)
gsub.c:720: error: ‘GL_UNSIGNED_BYTE’ undeclared (first use in this function)
gsub.c:778: error: ‘GL_COMPILE_AND_EXECUTE’ undeclared (first use in this function)
gsub.c:833: error: ‘GL_QUADS’ undeclared (first use in this function)
gsub.c: In function ‘argDispImageTex3’:
gsub.c:909: error: ‘GL_TEXTURE_2D’ undeclared (first use in this function)
gsub.c:910: error: ‘GL_TEXTURE’ undeclared (first use in this function)
gsub.c:912: error: ‘GL_MODELVIEW’ undeclared (first use in this function)
gsub.c:914: error: ‘glid’ undeclared (first use in this function)
gsub.c:919: error: ‘GL_UNPACK_ROW_LENGTH’ undeclared (first use in this function)
gsub.c:937: error: ‘GL_RGB_EXT’ undeclared (first use in this function)
gsub.c:937: error: ‘GL_UNSIGNED_BYTE’ undeclared (first use in this function)
gsub.c:994: error: ‘GL_COMPILE_AND_EXECUTE’ undeclared (first use in this function)
gsub.c:1058: error: ‘GL_QUADS’ undeclared (first use in this function)
gsub.c: In function ‘argDispHalfImage’:
gsub.c:1249: error: ‘GL_SCISSOR_TEST’ undeclared (first use in this function)
gsub.c: In function ‘argDispHalfImageDrawPixels’:
gsub.c:1259: error: ‘GLfloat’ undeclared (first use in this function)
gsub.c:1259: error: expected ‘;’ before ‘zoom’
gsub.c:1262: error: ‘zoom’ undeclared (first use in this function)
gsub.c:1294: error: ‘GL_RGB_EXT’ undeclared (first use in this function)
gsub.c:1294: error: ‘GL_UNSIGNED_BYTE’ undeclared (first use in this function)
gsub.c: In function ‘argDispHalfImageTex’:
gsub.c:1359: error: ‘GL_TEXTURE_2D’ undeclared (first use in this function)
gsub.c:1360: error: ‘GL_TEXTURE’ undeclared (first use in this function)
gsub.c:1362: error: ‘GL_MODELVIEW’ undeclared (first use in this function)
gsub.c:1364: error: ‘glid’ undeclared (first use in this function)
gsub.c:1369: error: ‘GL_UNPACK_ROW_LENGTH’ undeclared (first use in this function)
gsub.c:1387: error: ‘GL_RGB_EXT’ undeclared (first use in this function)
gsub.c:1387: error: ‘GL_UNSIGNED_BYTE’ undeclared (first use in this function)
gsub.c:1444: error: ‘GL_COMPILE_AND_EXECUTE’ undeclared (first use in this function)
gsub.c:1499: error: ‘GL_QUADS’ undeclared (first use in this function)
gsub.c: In function ‘argLineSeg’:
gsub.c:1553: error: ‘GL_LINES’ undeclared (first use in this function)
gsub.c: In function ‘argLineSegHMD’:
gsub.c:1576: error: ‘GL_LINES’ undeclared (first use in this function)
gsub.c: In function ‘argInitStencil’:
gsub.c:1588: error: ‘GL_STENCIL_TEST’ undeclared (first use in this function)
gsub.c:1590: error: ‘GL_STENCIL_BUFFER_BIT’ undeclared (first use in this function)
gsub.c:1596: error: ‘GL_ALWAYS’ undeclared (first use in this function)
gsub.c:1597: error: ‘GL_REPLACE’ undeclared (first use in this function)
gsub.c:1598: error: ‘GL_LINES’ undeclared (first use in this function)
gsub.c:1634: error: ‘GL_KEEP’ undeclared (first use in this function)
gsub.c: In function ‘argSetStencil’:
gsub.c:1650: error: ‘GL_STENCIL_TEST’ undeclared (first use in this function)
gsub.c:1651: error: ‘GL_ALWAYS’ undeclared (first use in this function)
gsub.c:1652: error: ‘GL_KEEP’ undeclared (first use in this function)
gsub.c:1656: error: ‘GL_EQUAL’ undeclared (first use in this function)
make[2]: *** [../../libARgsub.a(gsub.o)] Error 1
make[2]: Leaving directory `/tmp/ARToolKit/lib/SRC/Gl'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/ARToolKit/lib/SRC'
make: *** [all] Error 2
josh@Uber-Computer:/tmp/ARToolKit$ sudo make install
Password:
make: *** No rule to make target `install'. Stop.
josh@Uber-Computer:/tmp/ARToolKit$ 

```

Didn't work. Program not me?

---

### Post by lamego on 2007-01-21
You need to install the opengl development files.
```
sudo apt-get install libglut3-dev
```

---

### Post by jtreach on 2007-01-21
```
josh@Uber-Computer:~$ sudo apt-get install libglut3-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdebase-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  freeglut3-dev libgl1-mesa-dev libglu1-mesa-dev libice-dev libsm-dev
  libx11-dev libxau-dev libxdmcp-dev libxext-dev libxt-dev mesa-common-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  xlibmesa-gl-dev xtrans-dev
The following NEW packages will be installed
  freeglut3-dev libgl1-mesa-dev libglu1-mesa-dev libglut3-dev libice-dev
  libsm-dev libx11-dev libxau-dev libxdmcp-dev libxext-dev libxt-dev
  mesa-common-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  x11proto-xext-dev xlibmesa-gl-dev xtrans-dev
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 2736kB of archives.
After unpacking 11.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com edgy/main x11proto-core-dev 7.0.7-1 [78.3kB]
Get: 2 http://gb.archive.ubuntu.com edgy/main libice-dev 2:1.0.1-1ubuntu1 [49.9kB]
Get: 3 http://gb.archive.ubuntu.com edgy/main libsm-dev 2:1.0.1-1ubuntu1 [20.0kB]
Get: 4 http://gb.archive.ubuntu.com edgy/main libxau-dev 1:1.0.1-1 [10.3kB]
Get: 5 http://gb.archive.ubuntu.com edgy/main libxdmcp-dev 1:1.0.1-1 [13.6kB]
Get: 6 http://gb.archive.ubuntu.com edgy/main x11proto-input-dev 1.3.2-3ubuntu1 [13.4kB]
Get: 7 http://gb.archive.ubuntu.com edgy/main x11proto-xext-dev 7.0.2-4ubuntu1 [41.7kB]
Get: 8 http://gb.archive.ubuntu.com edgy/main x11proto-kb-dev 1.0.3-0ubuntu1 [26.5kB]
Get: 9 http://gb.archive.ubuntu.com edgy/main xtrans-dev 1.0.1-1 [58.8kB]
Get: 10 http://gb.archive.ubuntu.com edgy/main libx11-dev 2:1.0.3-0ubuntu4 [1181kB]
Get: 11 http://gb.archive.ubuntu.com edgy/main libxext-dev 2:1.0.1-1ubuntu1 [73.7kB]
Get: 12 http://gb.archive.ubuntu.com edgy/main libxt-dev 1:1.0.2-1ubuntu1 [476kB]
Get: 13 http://gb.archive.ubuntu.com edgy/main mesa-common-dev 6.5.1~20060817-0ubuntu3 [176kB]
Get: 14 http://gb.archive.ubuntu.com edgy/main libgl1-mesa-dev 6.5.1~20060817-0ubuntu3 [50.1kB]
Get: 15 http://gb.archive.ubuntu.com edgy-updates/main xlibmesa-gl-dev 1:7.1.1ubuntu6.2 [17.5kB]
Get: 16 http://gb.archive.ubuntu.com edgy/main libglu1-mesa-dev 6.5.1~20060817-0ubuntu3 [273kB]
Get: 17 http://gb.archive.ubuntu.com edgy/main freeglut3-dev 2.4.0-5 [155kB]   
Get: 18 http://gb.archive.ubuntu.com edgy/main libglut3-dev 3.7-25 [21.5kB]    
Fetched 2736kB in 23s (114kB/s)                                                
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 102291 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.7-1_all.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.1-1_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.1-1_i386.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.3.2-3ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-0ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.1-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.0.3-0ubuntu4_i386.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_6.5.1~20060817-0ubuntu3_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.5.1~20060817-0ubuntu3_i386.deb) ...
Selecting previously deselected package xlibmesa-gl-dev.
Unpacking xlibmesa-gl-dev (from .../xlibmesa-gl-dev_1%3a7.1.1ubuntu6.2_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_6.5.1~20060817-0ubuntu3_i386.deb) ...
Selecting previously deselected package freeglut3-dev.
Unpacking freeglut3-dev (from .../freeglut3-dev_2.4.0-5_i386.deb) ...
Selecting previously deselected package libglut3-dev.
Unpacking libglut3-dev (from .../libglut3-dev_3.7-25_all.deb) ...
Setting up x11proto-core-dev (7.0.7-1) ...
Setting up libice-dev (1.0.1-1ubuntu1) ...
Setting up libsm-dev (1.0.1-1ubuntu1) ...
Setting up libxau-dev (1.0.1-1) ...
Setting up libxdmcp-dev (1.0.1-1) ...
Setting up x11proto-input-dev (1.3.2-3ubuntu1) ...
Setting up x11proto-xext-dev (7.0.2-4ubuntu1) ...
Setting up x11proto-kb-dev (1.0.3-0ubuntu1) ...
Setting up xtrans-dev (1.0.1-1) ...
Setting up mesa-common-dev (6.5.1~20060817-0ubuntu3) ...
Setting up libgl1-mesa-dev (6.5.1~20060817-0ubuntu3) ...
Setting up xlibmesa-gl-dev (7.1.1ubuntu6.2) ...
Setting up libglu1-mesa-dev (6.5.1~20060817-0ubuntu3) ...
Setting up libxext-dev (1.0.1-1ubuntu1) ...
Setting up libx11-dev (1.0.3-0ubuntu4) ...
Setting up libxt-dev (1.0.2-1ubuntu1) ...
Setting up freeglut3-dev (2.4.0-5) ...
Setting up libglut3-dev (3.7-25) ...
josh@Uber-Computer:~$ cd /
josh@Uber-Computer:/$ cd tmp
josh@Uber-Computer:/tmp$ /josh
bash: /josh: No such file or directory
josh@Uber-Computer:/tmp$ cd /
josh@Uber-Computer:/$ cd /home
josh@Uber-Computer:/home$ cd /josh
bash: cd: /josh: No such file or directory
josh@Uber-Computer:/home$ /Josh
bash: /Josh: No such file or directory
josh@Uber-Computer:/home$ cd josh
josh@Uber-Computer:~$ cd ARToolkit
bash: cd: ARToolkit: No such file or directory
josh@Uber-Computer:~$ cd /
josh@Uber-Computer:/$ cd /home
josh@Uber-Computer:/home$ cd /josh
bash: cd: /josh: No such file or directory
josh@Uber-Computer:/home$ cd josh
josh@Uber-Computer:~$ cd .ARToolkit
josh@Uber-Computer:~/.ARToolkit$ cd ARToolKit
josh@Uber-Computer:~/.ARToolkit/ARToolKit$ ./configure
bash: ./configure: No such file or directory
josh@Uber-Computer:~/.ARToolkit/ARToolKit$ ./Configure
Select a video capture driver.
  1: Video4Linux
  2: Video4Linux+JPEG Decompression (EyeToy)
  3: Digital Video Camcoder through IEEE 1394 (DV Format)
  4: Digital Video Camera through IEEE 1394 (VGA NONCOMPRESSED Image Format)
  5: GStreamer Media Framework
Enter : 2
Do you want to create debug symbols? (y or n)
Enter : n
Build gsub libraries with texture rectangle support? (y or n)
GL_NV_texture_rectangle is supported on most NVidia graphics cards
and on ATi Radeon and better graphics cards
Enter : y
  create ./Makefile
  create lib/SRC/Makefile
  create lib/SRC/AR/Makefile
  create lib/SRC/ARMulti/Makefile
  create lib/SRC/Gl/Makefile
  create lib/SRC/VideoLinux1394Cam/Makefile
  create lib/SRC/VideoLinuxDV/Makefile
  create lib/SRC/VideoLinuxV4L/Makefile
  create lib/SRC/VideoSGI/Makefile
  create lib/SRC/VideoMacOSX/Makefile
  create lib/SRC/VideoGStreamer/Makefile
  create lib/SRC/ARvrml/Makefile
  create util/Makefile
  create util/calib_camera2/Makefile
  create util/calib_cparam/Makefile
  create util/calib_distortion/Makefile
  create util/mk_patt/Makefile
  create util/graphicsTest/Makefile
  create util/videoTest/Makefile
  create examples/Makefile
  create examples/collide/Makefile
  create examples/exview/Makefile
  create examples/loadMultiple/Makefile
  create examples/modeTest/Makefile
  create examples/multi/Makefile
  create examples/optical/Makefile
  create examples/paddle/Makefile
  create examples/paddleDemo/Makefile
  create examples/paddleInteraction/Makefile
  create examples/range/Makefile
  create examples/relation/Makefile
  create examples/simple/Makefile
  create examples/simple2/Makefile
  create examples/simpleLite/Makefile
  create examples/twoView/Makefile
  create examples/simpleVRML/Makefile
  create include/AR/config.h
Done.
josh@Uber-Computer:~/.ARToolkit/ARToolKit$ install
install: missing file operand
Try `install --help' for more information.
josh@Uber-Computer:~/.ARToolkit/ARToolKit$ make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/AR'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAlloc.c
ar rs ../../libAR.a mAlloc.o
rm -f mAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mFree.c
ar rs ../../libAR.a mFree.o
rm -f mFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocDup.c
ar rs ../../libAR.a mAllocDup.o
rm -f mAllocDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDup.c
ar rs ../../libAR.a mDup.o
rm -f mDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocTrans.c
ar rs ../../libAR.a mAllocTrans.o
rm -f mAllocTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mTrans.c
ar rs ../../libAR.a mTrans.o
rm -f mTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocMul.c
ar rs ../../libAR.a mAllocMul.o
rm -f mAllocMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mMul.c
ar rs ../../libAR.a mMul.o
rm -f mMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocInv.c
ar rs ../../libAR.a mAllocInv.o
rm -f mAllocInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mInv.c
ar rs ../../libAR.a mInv.o
rm -f mInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mSelfInv.c
ar rs ../../libAR.a mSelfInv.o
rm -f mSelfInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocUnit.c
ar rs ../../libAR.a mAllocUnit.o
rm -f mAllocUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mUnit.c
ar rs ../../libAR.a mUnit.o
rm -f mUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDisp.c
ar rs ../../libAR.a mDisp.o
rm -f mDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDet.c
ar rs ../../libAR.a mDet.o
rm -f mDet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mPCA.c
ar rs ../../libAR.a mPCA.o
rm -f mPCA.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vAlloc.c
ar rs ../../libAR.a vAlloc.o
rm -f vAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vDisp.c
ar rs ../../libAR.a vDisp.o
rm -f vDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vFree.c
ar rs ../../libAR.a vFree.o
rm -f vFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vHouse.c
ar rs ../../libAR.a vHouse.o
rm -f vHouse.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vInnerP.c
ar rs ../../libAR.a vInnerP.o
rm -f vInnerP.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vTridiag.c
ar rs ../../libAR.a vTridiag.o
rm -f vTridiag.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramGet.c
ar rs ../../libAR.a paramGet.o
rm -f paramGet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDecomp.c
ar rs ../../libAR.a paramDecomp.o
rm -f paramDecomp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDistortion.c
ar rs ../../libAR.a paramDistortion.o
rm -f paramDistortion.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramChangeSize.c
ar rs ../../libAR.a paramChangeSize.o
rm -f paramChangeSize.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramFile.c
ar rs ../../libAR.a paramFile.o
rm -f paramFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDisp.c
ar rs ../../libAR.a paramDisp.o
rm -f paramDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker.c
ar rs ../../libAR.a arDetectMarker.o
rm -f arDetectMarker.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat.c
ar rs ../../libAR.a arGetTransMat.o
rm -f arGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat2.c
ar rs ../../libAR.a arGetTransMat2.o
rm -f arGetTransMat2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat3.c
ar rs ../../libAR.a arGetTransMat3.o
rm -f arGetTransMat3.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMatCont.c
ar rs ../../libAR.a arGetTransMatCont.o
rm -f arGetTransMatCont.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arLabeling.c
ar rs ../../libAR.a arLabeling.o
rm -f arLabeling.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker2.c
ar rs ../../libAR.a arDetectMarker2.o
rm -f arDetectMarker2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetMarkerInfo.c
ar rs ../../libAR.a arGetMarkerInfo.o
rm -f arGetMarkerInfo.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetCode.c
ar rs ../../libAR.a arGetCode.o
rm -f arGetCode.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arUtil.c
arUtil.c: In function &#8216;arGetVersion&#8217;:
arUtil.c:46: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ar rs ../../libAR.a arUtil.o
rm -f arUtil.o
make[2]: Leaving directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/ARMulti'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiReadConfigFile.c
ar rs ../../libARMulti.a arMultiReadConfigFile.o
rm -f arMultiReadConfigFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiGetTransMat.c
ar rs ../../libARMulti.a arMultiGetTransMat.o
rm -f arMultiGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiActivate.c
ar rs ../../libARMulti.a arMultiActivate.o
rm -f arMultiActivate.o
make[2]: Leaving directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/Gl'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include gsub.c
ar rs ../../libARgsub.a gsub.o
ar: creating ../../libARgsub.a
rm -f gsub.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include gsubUtil.c
ar rs ../../libARgsubUtil.a gsubUtil.o
ar: creating ../../libARgsubUtil.a
rm -f gsubUtil.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include gsub_lite.c
gsub_lite.c: In function &#8216;arglCameraFrustum&#8217;:
gsub_lite.c:678: warning: passing argument 1 of &#8216;arParamDecompMat&#8217; from incompatible pointer type
gsub_lite.c: In function &#8216;arglCameraFrustumRH&#8217;:
gsub_lite.c:737: warning: passing argument 1 of &#8216;arParamDecompMat&#8217; from incompatible pointer type
ar rs ../../libARgsub_lite.a gsub_lite.o
ar: creating ../../libARgsub_lite.a
rm -f gsub_lite.o
make[2]: Leaving directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/Gl'
(cd VideoLinuxV4L; make -f Makefile)
make[2]: Entering directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/VideoLinuxV4L'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include video.c
In file included from video.c:36:
jpegtorgb.h:27:21: error: jpeglib.h: No such file or directory
jpegtorgb.h:28:20: error: jerror.h: No such file or directory
In file included from video.c:36:
jpegtorgb.h:50: error: field &#8216;pub&#8217; has incomplete type
jpegtorgb.h:54: error: expected specifier-qualifier-list before &#8216;JOCTET&#8217;
jpegtorgb.h: In function &#8216;METHODDEF&#8217;:
jpegtorgb.h:68: error: expected declaration specifiers before &#8216;EyeToy_init_source&#8217;
jpegtorgb.h:112: error: expected declaration specifiers before &#8216;METHODDEF&#8217;
jpegtorgb.h:137: error: expected declaration specifiers before &#8216;METHODDEF&#8217;
jpegtorgb.h:176: error: expected declaration specifiers before &#8216;METHODDEF&#8217;
jpegtorgb.h:189: error: expected declaration specifiers before &#8216;GLOBAL&#8217;
jpegtorgb.h:221: error: storage class specified for parameter &#8216;TransfertBufferImage&#8217;
jpegtorgb.h:226: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
jpegtorgb.h:232: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:41: error: storage class specified for parameter &#8216;gVid&#8217;
video.c:41: error: parameter &#8216;gVid&#8217; is initialized
video.c:44: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:49: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:61: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:72: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:79: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:86: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:93: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:100: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:109: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:147: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:511: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:525: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:545: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:558: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:574: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:610: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
video.c:615: error: old-style parameter declarations in prototyped function definition
video.c:615: error: expected &#8216;{&#8217; at end of input
make[2]: *** [../../libARvideo.a(video.o)] Error 1
make[2]: Leaving directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC/VideoLinuxV4L'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/josh/.ARToolkit/ARToolKit/lib/SRC'
make: *** [all] Error 2
josh@Uber-Computer:~/.ARToolkit/ARToolKit$ sudo make install
make: *** No rule to make target `install'. Stop.
josh@Uber-Computer:~/.ARToolkit/ARToolKit$ 


```

:(

---

### Post by jtreach on 2007-01-21
From the Read Me thought it might be useful.

Building on Linux / SGI Irix.
-----------------------------

Prerequisites:
 *  (Optional, for VRML renderer only) openvrml-0.16.1 and dependencies. Download from [http://sf.net/projects/openvrml](http://sf.net/projects/openvrml).
 
Unpack the ARToolKit to a convenient location. The root of this location will be referred to below as {ARToolKit}:
    tar zxvf ARToolKit-2.72.tgz
Configure and build. The Linux builds support video input using either Video4Linux, an IIDC-compliant or DV camera connected via IEEE-1394, or a Sony EyeToy camera connected via USB. Alternatively you can use GStreamer 0.10 (0.8 is not supported and also not recommended) as input method. This requires you to install the gstreamer development packages for your Linux distribution. You will be prompted as to which of the four Linux video drivers you wish to use at the Configure step.
    cd {ARToolKit}
    ./Configure
	make
Following a successful build, to run a binary such as simpleTest:
	cd {ARToolKit}/bin
	./simpleTest

The VRML renderering library and example (libARvrml & simpleVRML) are optional builds:
	cd {ARToolKit}/lib/SRC/ARvrml
	make
	cd {ARToolKit}/examples/simpleVRML
	make
	cd {ARToolKit}/bin
	./simpleVRML

---

### Post by radicaledward on 2007-03-20
*bump*

I'm having a similar problem. Can anyone help?

```
panzer@TheMAGI:~/Desktop/ARToolKit$ make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/panzer/Desktop/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/panzer/Desktop/ARToolKit/lib/SRC/AR'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAlloc.c
ar rs ../../libAR.a mAlloc.o
rm -f mAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mFree.c
ar rs ../../libAR.a mFree.o
rm -f mFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocDup.c
ar rs ../../libAR.a mAllocDup.o
rm -f mAllocDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDup.c
ar rs ../../libAR.a mDup.o
rm -f mDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocTrans.c
ar rs ../../libAR.a mAllocTrans.o
rm -f mAllocTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mTrans.c
ar rs ../../libAR.a mTrans.o
rm -f mTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocMul.c
ar rs ../../libAR.a mAllocMul.o
rm -f mAllocMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mMul.c
ar rs ../../libAR.a mMul.o
rm -f mMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocInv.c
ar rs ../../libAR.a mAllocInv.o
rm -f mAllocInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mInv.c
ar rs ../../libAR.a mInv.o
rm -f mInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mSelfInv.c
ar rs ../../libAR.a mSelfInv.o
rm -f mSelfInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocUnit.c
ar rs ../../libAR.a mAllocUnit.o
rm -f mAllocUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mUnit.c
ar rs ../../libAR.a mUnit.o
rm -f mUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDisp.c
ar rs ../../libAR.a mDisp.o
rm -f mDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDet.c
ar rs ../../libAR.a mDet.o
rm -f mDet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mPCA.c
ar rs ../../libAR.a mPCA.o
rm -f mPCA.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vAlloc.c
ar rs ../../libAR.a vAlloc.o
rm -f vAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vDisp.c
ar rs ../../libAR.a vDisp.o
rm -f vDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vFree.c
ar rs ../../libAR.a vFree.o
rm -f vFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vHouse.c
ar rs ../../libAR.a vHouse.o
rm -f vHouse.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vInnerP.c
ar rs ../../libAR.a vInnerP.o
rm -f vInnerP.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vTridiag.c
ar rs ../../libAR.a vTridiag.o
rm -f vTridiag.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramGet.c
ar rs ../../libAR.a paramGet.o
rm -f paramGet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDecomp.c
ar rs ../../libAR.a paramDecomp.o
rm -f paramDecomp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDistortion.c
ar rs ../../libAR.a paramDistortion.o
rm -f paramDistortion.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramChangeSize.c
ar rs ../../libAR.a paramChangeSize.o
rm -f paramChangeSize.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramFile.c
ar rs ../../libAR.a paramFile.o
rm -f paramFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDisp.c
ar rs ../../libAR.a paramDisp.o
rm -f paramDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker.c
ar rs ../../libAR.a arDetectMarker.o
rm -f arDetectMarker.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat.c
ar rs ../../libAR.a arGetTransMat.o
rm -f arGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat2.c
ar rs ../../libAR.a arGetTransMat2.o
rm -f arGetTransMat2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat3.c
ar rs ../../libAR.a arGetTransMat3.o
rm -f arGetTransMat3.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMatCont.c
ar rs ../../libAR.a arGetTransMatCont.o
rm -f arGetTransMatCont.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arLabeling.c
ar rs ../../libAR.a arLabeling.o
rm -f arLabeling.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker2.c
ar rs ../../libAR.a arDetectMarker2.o
rm -f arDetectMarker2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetMarkerInfo.c
ar rs ../../libAR.a arGetMarkerInfo.o
rm -f arGetMarkerInfo.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetCode.c
ar rs ../../libAR.a arGetCode.o
rm -f arGetCode.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arUtil.c
arUtil.c: In function ‘arGetVersion’:
arUtil.c:46: warning: incompatible implicit declaration of built-in function ‘exit’
ar rs ../../libAR.a arUtil.o
rm -f arUtil.o
make[2]: Leaving directory `/home/panzer/Desktop/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/home/panzer/Desktop/ARToolKit/lib/SRC/ARMulti'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiReadConfigFile.c
ar rs ../../libARMulti.a arMultiReadConfigFile.o
rm -f arMultiReadConfigFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiGetTransMat.c
ar rs ../../libARMulti.a arMultiGetTransMat.o
rm -f arMultiGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arMultiActivate.c
ar rs ../../libARMulti.a arMultiActivate.o
rm -f arMultiActivate.o
make[2]: Leaving directory `/home/panzer/Desktop/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/home/panzer/Desktop/ARToolKit/lib/SRC/Gl'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include gsub.c
ar rs ../../libARgsub.a gsub.o
rm -f gsub.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include gsubUtil.c
ar rs ../../libARgsubUtil.a gsubUtil.o
rm -f gsubUtil.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include gsub_lite.c
gsub_lite.c: In function ‘arglCameraFrustum’:
gsub_lite.c:659: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
gsub_lite.c: In function ‘arglCameraFrustumRH’:
gsub_lite.c:718: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
ar rs ../../libARgsub_lite.a gsub_lite.o
rm -f gsub_lite.o
make[2]: Leaving directory `/home/panzer/Desktop/ARToolKit/lib/SRC/Gl'
(cd VideoLinuxV4L; make -f Makefile)
make[2]: Entering directory `/home/panzer/Desktop/ARToolKit/lib/SRC/VideoLinuxV4L'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include video.c
In file included from video.c:36:
jpegtorgb.h:27:21: error: jpeglib.h: No such file or directory
jpegtorgb.h:28:20: error: jerror.h: No such file or directory
In file included from video.c:36:
jpegtorgb.h:50: error: field ‘pub’ has incomplete type
jpegtorgb.h:54: error: expected specifier-qualifier-list before ‘JOCTET’
jpegtorgb.h: In function ‘METHODDEF’:
jpegtorgb.h:68: error: expected declaration specifiers before ‘EyeToy_init_source’
jpegtorgb.h:112: error: expected declaration specifiers before ‘METHODDEF’
jpegtorgb.h:137: error: expected declaration specifiers before ‘METHODDEF’
jpegtorgb.h:176: error: expected declaration specifiers before ‘METHODDEF’
jpegtorgb.h:189: error: expected declaration specifiers before ‘GLOBAL’
jpegtorgb.h:221: error: storage class specified for parameter ‘TransfertBufferImage’
jpegtorgb.h:226: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
jpegtorgb.h:232: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:41: error: storage class specified for parameter ‘gVid’
video.c:41: error: parameter ‘gVid’ is initialized
video.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:61: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:72: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:79: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:93: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:147: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:511: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:525: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:545: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:558: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:574: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:614: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
video.c:619: error: old-style parameter declarations in prototyped function definition
video.c:619: error: expected ‘{’ at end of input
make[2]: *** [../../libARvideo.a(video.o)] Error 1
make[2]: Leaving directory `/home/panzer/Desktop/ARToolKit/lib/SRC/VideoLinuxV4L'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/panzer/Desktop/ARToolKit/lib/SRC'
make: *** [all] Error 2
panzer@TheMAGI:~/Desktop/ARToolKit$ 
```

---


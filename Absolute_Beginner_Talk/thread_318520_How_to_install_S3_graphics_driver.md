---
title: "How to: install S3 graphics driver"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Snader on 2006-12-14
Hello,

For example. Every time I scroll down a page in Mozilla, it takes a lot of time (1 sec.) to build up the display. Which makes me guess, that my graphic card isn't working properly.

I identified the chip (86C380 Twister (8D01), 86C381 TwisterT (8D01))  and found the right Linux drivers for my videocard:
[http://www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp#id_380drv](http://www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp#id_380drv)

1) Do I really need to install these?
2) And if yes, how? Because I have really no idea, what to do with the " Savage_4.1.0_binary.tgz" or the two files in it. And I wasn't able to find any documentation on it.

Thanks in advance for your time.

Sander

---

### Post by Snader on 2006-12-14
Additional information:
When looking in the "/usr/X11R6/lib/X11" folder, I only see two directories: "fonts" and "xkb" and no files.

I don't know the exact value of this information. But regarding to other topics, this information sometimes leads to solutions.

---

### Post by Kobalt on 2006-12-14
Here is a HowTo for installing drivers of Savage video cards : > [http://www.ubuntuforums.org/showthread.php?t=75393](http://www.ubuntuforums.org/showthread.php?t=75393)

---

### Post by Snader on 2006-12-14
Thank you very much!! I'm going to try this.

---

### Post by Snader on 2006-12-14
The first command: sudo apt-get install gcc-3.4 build-essential, worked very well.
But the second: sudo apt-get install linux-headers-2.6.12-10-386, gives an error.

It says:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.12-10-386

BTW: There is nothing wrong with the internet connection, no proxy either. Maybe the version number has changed?

---

### Post by zgornel on 2006-12-14
Have you tried putting in /etc/X11/xorg.conf , in Section "Device", Driver "savage" ?
If you do ```
man savage
``` you'll see that the driver supports 
```
Twister (ProSavage PN133)
                       (8d01) (2D, 3D)

```

---

### Post by VividHazE on 2006-12-14
Have you enabled the Universe and Multiverse repositories? Go to Synaptic Package Manger, then up in one of the titlebar menus you'll find Repositories, just select them all and reload the package list.

---

### Post by Snader on 2006-12-14
> **zgornel said:**
> Have you tried putting in /etc/X11/xorg.conf , in Section "Device", Driver "savage" ?
This worked out very well! The screen builds up fast and everything runs very smooth. Thanks a lot!

Dispite of all your effort, I still remain with some questions:
1) Now that I've changed xorg.conf, is my grapics card fully functional? For instance, does it support 3D-graphics (OpenGL) now? Additional Information: "glxgears -printfps" renders about 95 fps. Which is the same as it did before changing xorg.conf.
2) What if I had chosen for the solution of Kobalt? Would that have made any difference? Because I'm a bit confused getting two different solutions...
3) If the solution of Kobalt doesn't have any advantages. Is it true, that I can conclude that the installation of: "sudo apt-get install gcc-3.4 build-essential" is now useless? And if yes, how can I make it undone?

Sorry for all those questions and thanks a lot again for all the effort.

Best regards,

Sander

---

### Post by Snader on 2006-12-14
> **VividHazE said:**
> Have you enabled the Universe and Multiverse repositories? Go to Synaptic Package Manger, then up in one of the titlebar menus you'll find Repositories, just select them all and reload the package list.
For the record. I do have universe, main,  multiverse and restricted checked (which is default).

---

### Post by zgornel on 2006-12-14
Write in a terminal : ```
glxinfo |grep direct
``` If you see "yes" in the direct rendering line, you have 3d support and you won't have to do anything. 
If you don't have direct rendering, use the tutorial but, install the latest linux-headers package (find it in synaptic). That tutorial is rather old and Edgy has a different version of the kernel headers.

---

### Post by Snader on 2006-12-14
It said:
```
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```
So I proceeded with the solution of Kobalt.

Although I thought it should be a cakewalk now, I guess I'm making a stupid mistake. The install via Synaptec of the linux-headers worked out well. But these five lines don't:
```
wget http://dri.freedesktop.org/snapshots/archive/common-20051127-linux.i386.tar.bz2 
wget http://dri.freedesktop.org/snapshots/archive/savage-20051125-linux.i386.tar.bz2 
tar -xjf common-20051127-linux.i386.tar.bz2 
tar -xjf savage-20051125-linux.i386.tar.bz2  
cd dripkg 
sudo ./install.sh
```
The first four make me download these two tar's to my /home/[username]. Then it extracts them, giving the directories the same name as the tar's. As you can guess, "cd dripkg" gives me the error that this directory doesn't exist and so I can't proceed. What is going wrong?

Another two questions:
1) Do I need to set back my xorg.conf? As I changed the device driver.
2) Was it right to install: gcc-3.4 build-essential, common-20051127 and savage-20051125. Or were there newer versions that make a difference?

Thanks again! I really appreciate all your help and the incredible response time.

---

### Post by zgornel on 2006-12-15
No, you do not need to set back xorg.conf, The new driver you are about to install is still called savage so leae xorg.conf. Edgy comes with gcc 4.1 but if had no gcc installed before, gcc 3.4 will work fine (otherwise, uninstall it and install the build-essential package). The build-esential package will intall all the prerequisite packages need to compile stuff. 
As for the savage drivers, go to [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) and download the latest common and savage archives (april 2006) and install them.

---

### Post by Snader on 2006-12-15
I'll try that, when I'm back home.

1) How can I uninstall the old GCC? Should this be done via Synaptec?
2) And could you take a look at the problem with "cd dripkg" metioned in my previous post?

Again, thanks for helping! You have a lot of patience with me. I hope these will be my last questions. Next thing to do for me, is read lots and lots of information about Linux and get to understand it better.

---

### Post by zgornel on 2006-12-15
You should not install gcc 3.4 if you can compile sources with it. As for the dripkg problem, simply change the directory to the newly created dirs when extracted the archives. the sources will be there.

---

### Post by Snader on 2006-12-16
A problem occured.

The installation of the common-package went well. The savage-package gives me this:

```
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
```

This is shown in the log-file:
```
make DRM_MODULES=savage.o modules
make[1]: Entering directory `/home/sander/savage/drm/linux-core'
make -C /lib/modules/2.6.17-10-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/sander/savage/drm/linux-core/ati_pcigart.o
/home/sander/savage/drm/linux-core/ati_pcigart.c: In function ‘drm_ati_free_pcigart_table’:
/home/sander/savage/drm/linux-core/ati_pcigart.c:87: error: ‘struct page’ has no member named ‘count’
make[3]: *** [/home/sander/savage/drm/linux-core/ati_pcigart.o] Error 1
make[2]: *** [_module_/home/sander/savage/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/sander/savage/drm/linux-core'
make: *** [savage.o] Error 2
```

---

### Post by zgornel on 2006-12-16
I know the error. I got it too but i solved it by compiling Mesa 6.5.2 (it comes with the OpenGl libraries and drivers for i810/830/915, savage, 3dfx and other cards). You could try to compile it, the problem is it will give you a lot of missing headers, problems solved by installing packages I don't remember. 
What you can do is to: download, compile and install *libdrm* ( [http://dri.freedesktop.org/libdrm/](http://dri.freedesktop.org/libdrm/) ), info for install here: [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building) , section 1.3.
Then, install Mesa 6.5.2, find it here: [http://sourceforge.net/project/showfiles.php?group_id=3&package_id=2436](http://sourceforge.net/project/showfiles.php?group_id=3&package_id=2436) , Install instructions here: [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building) , section 1.4.

Basically, after downloading the Mesa6.5.2 (The MesaLib-6.5.2.tar.bz2), unpack it somewhere and enter the Mesa 6.5.2 dir. The following modiffications will be done in order to install Mesa to another directory rather than the default so installations will not interfear.
Here are the steps:
1. Go to the **configs** directory and do a ```
gedit ./default
``` Scroll to the last lines and edit them so they will look like: ```
INSTALL_DIR = /opt/mesa652 
``` and ```
DRI_DRIVER_INSTALL_DIR = /opt/mesa652/
``` This assures that after the installation, you will find the drivers (savage driver) and opengl libraries in /opt/mesa652.
2. In the same configs dir, ```
gedit ./linux-dri
``` Go to the last line, and edit it so it will look like ```
 DRI_DIRS = savage 
``` . This specifies to the compiler to compile only the savage driver. You will only need this driver.
3. Return to the main dir ```
cd ..
```. Run ```
make linux-dri-x86
```. Compilation of the drivers and libraries will start but most probably will stop due to some mising headers. I remember installing 3-4 dev packages with synaptic and solving this problem. What you can do is see the exact error and search in synaptic a package that resembles the header name. Should not be too hard.
4. If installation terminates sucessfully, run ```
sudo make install
```. All will be installed in /opt/mesa652.
5. The final step is to specify X to use these drivers and opengl libraries instead of the default ones. In order to do that, add these 3 lines to ~/.bashrc :
```
export LIBGL_DRIVERS_PATH=/opt/mesa652/
export LD_PRELOAD=/opt/mesa652/lib/libGL.so.1
export LD_LIBRARY_PATH=/opt/mesa652/lib/

```
6. Log off and relog in. Run a ```
glxinfo
```. The drivers should be from 2006 and and Mesa version 6.5.2.

---

### Post by Snader on 2006-12-16
Nice discription you wrote for me! But I still managed to get myself stuck, right at the very beginning.

I downloaded the "libdrm-2.3.0.tar.bz2" (and some others) and extracted the contents. As descriped in "1.3. Building libdrm" I should open the extracted directory and run "./autogen.sh". Problem is, there is no such file in the directory. There is a "install-sh" there. So I tried "sudo ./install-sh", but without succes.

Could you help me out once more? Thanks in advance.

Sander

```
sander@sander-laptop:~/libdrm-2.3.0$ dir
aclocal.m4    configure     install-sh    ltmain.sh    missing
config.guess  configure.ac  libdrm        Makefile.am  README
config.sub    depcomp       libdrm.pc.in  Makefile.in  shared-core
sander@sander-laptop:~/libdrm-2.3.0$ sudo ./install-sh
Password:
./install-sh: no input file specified.
```

---

### Post by zgornel on 2006-12-16
To install libdrm (required by Mesa), go into the libdrm dir and do directly:```
./configure --prefix=/usr
``` and then, ```
make install
``` I think it's an old wiki and things might have changed a bit ;) . It is written in the README. :D

---

### Post by Snader on 2006-12-17
Although it's an old Wiki, I think it's still correct. Also, I did read README. But I thought the default installation was good, instead of replacing the system copy. ;)

I have installed libdrm and checked the intallation with: "pkg-config --modversion libdrm". It said "2.3.0" so there is no doubt about that.

Then I tried to install Mesa 6.5.2, but as you predicted I got some errors. I read the errors a couple of times, but I really don't understand them.
As you told me, it must have something to do with some missing headers. So I read the FAQ and found a list of headers I need. Problem is, I couldn't find them with Synaptec... Maybe I'm using the wrong words in the search-function?

List of needed headers:
```
    * /usr/include/GL/gl.h - the main OpenGL header
    * /usr/include/GL/glu.h - the OpenGL GLU (utility) header
    * /usr/include/GL/glx.h - the OpenGL GLX header
    * /usr/include/GL/glext.h - the OpenGL extensions header
    * /usr/include/GL/glxext.h - the OpenGL GLX extensions header
    * /usr/include/GL/osmesa.h - the Mesa off-screen rendering header
    * /usr/lib/libGL.so - a symlink to libGL.so.1
    * /usr/lib/libGL.so.1 - a symlink to libGL.so.1.xyz
    * /usr/lib/libGL.so.xyz - the actual OpenGL/Mesa library. xyz denotes the Mesa version number.
    * /usr/lib/libGLU.so - a symlink to libGLU.so.1
    * /usr/lib/libGLU.so.1 - a symlink to libGLU.so.1.3.xyz
    * /usr/lib/libGLU.so.xyz - the OpenGL Utility library. xyz denotes the Mesa version number. 
```

The errors I get:
```
        not in ../../../src/mesa/glapi/stddef.h
        not in ../../../src/mesa/drivers/dri/common/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/stdlib.h, line 33): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in ../../../src/mesa/drivers/dri/common/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/alloca.h, line 25): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in ../../../src/mesa/drivers/dri/common/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/stdio.h, line 34): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in ../../../src/mesa/drivers/dri/common/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/_G_config.h, line 14): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in ../../../src/mesa/drivers/dri/common/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/wchar.h, line 48): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in ../../../src/mesa/drivers/dri/common/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/gconv.h, line 31): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in ../../../src/mesa/drivers/dri/common/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/libio.h, line 53): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../include/stdarg.h
        not in ../../../include/GL/internal/stdarg.h
        not in ../../../src/mesa/main/stdarg.h
        not in ../../../src/mesa/glapi/stdarg.h
        not in ../../../src/mesa/drivers/dri/common/stdarg.h
        not in /usr/include/drm/stdarg.h
        not in /usr/X11R6/include/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  clientattrib.c (reading glxclient.h, line 58): cannot find include file "GL/glxint.h"
        not in GL/glxint.h
        not in GL/glxint.h
        not in ./GL/glxint.h
        not in ../../../include/GL/glxint.h
        not in ../../../include/GL/internal/GL/glxint.h
        not in ../../../src/mesa/main/GL/glxint.h
        not in ../../../src/mesa/glapi/GL/glxint.h
        not in ../../../src/mesa/drivers/dri/common/GL/glxint.h
        not in /usr/include/drm/GL/glxint.h
        not in /usr/X11R6/include/GL/glxint.h
        not in /usr/include/GL/glxint.h
makedepend: warning:  clientattrib.c (reading glxclient.h, line 59): cannot find include file "GL/glxproto.h"
        not in GL/glxproto.h
        not in GL/glxproto.h
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in ../../../src/mesa/drivers/dri/common/GL/glxproto.h
        not in /usr/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  glxcmds.c, line 44: cannot find include file "X11/extensions/extutil.h"
        not in ./X11/extensions/extutil.h
        not in ../../../include/X11/extensions/extutil.h
        not in ../../../include/GL/internal/X11/extensions/extutil.h
        not in ../../../src/mesa/main/X11/extensions/extutil.h
        not in ../../../src/mesa/glapi/X11/extensions/extutil.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/extutil.h
        not in /usr/include/drm/X11/extensions/extutil.h
        not in /usr/X11R6/include/X11/extensions/extutil.h
        not in /usr/include/X11/extensions/extutil.h
makedepend: warning:  glxcmds.c, line 45: cannot find include file "X11/extensions/Xext.h"
        not in ./X11/extensions/Xext.h
        not in ../../../include/X11/extensions/Xext.h
        not in ../../../include/GL/internal/X11/extensions/Xext.h
        not in ../../../src/mesa/main/X11/extensions/Xext.h
        not in ../../../src/mesa/glapi/X11/extensions/Xext.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/Xext.h
        not in /usr/include/drm/X11/extensions/Xext.h
        not in /usr/X11R6/include/X11/extensions/Xext.h
        not in /usr/include/X11/extensions/Xext.h
makedepend: warning:  glxcmds.c (reading /usr/include/limits.h, line 125): cannot find include file "limits.h"
makedepend: warning:  glxcmds.c (reading ../../../src/mesa/main/glheader.h, line 72): cannot find include file "float.h"
        not in ./float.h
        not in ../../../include/float.h
        not in ../../../include/GL/internal/float.h
        not in ../../../src/mesa/main/float.h
        not in ../../../src/mesa/glapi/float.h
        not in ../../../src/mesa/drivers/dri/common/float.h
        not in /usr/include/drm/float.h
        not in /usr/X11R6/include/float.h
        not in /usr/include/float.h
makedepend: warning:  glxcmds.c (reading ../../../src/mesa/main/glheader.h, line 73): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../include/stdarg.h
        not in ../../../include/GL/internal/stdarg.h
        not in ../../../src/mesa/main/stdarg.h
        not in ../../../src/mesa/glapi/stdarg.h
        not in ../../../src/mesa/drivers/dri/common/stdarg.h
        not in /usr/include/drm/stdarg.h
        not in /usr/X11R6/include/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  glxext.c, line 49: cannot find include file "X11/extensions/Xext.h"
        not in ./X11/extensions/Xext.h
        not in ../../../include/X11/extensions/Xext.h
        not in ../../../include/GL/internal/X11/extensions/Xext.h
        not in ../../../src/mesa/main/X11/extensions/Xext.h
        not in ../../../src/mesa/glapi/X11/extensions/Xext.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/Xext.h
        not in /usr/include/drm/X11/extensions/Xext.h
        not in /usr/X11R6/include/X11/extensions/Xext.h
        not in /usr/include/X11/extensions/Xext.h
makedepend: warning:  glxext.c, line 50: cannot find include file "X11/extensions/extutil.h"
        not in ./X11/extensions/extutil.h
        not in ../../../include/X11/extensions/extutil.h
        not in ../../../include/GL/internal/X11/extensions/extutil.h
        not in ../../../src/mesa/main/X11/extensions/extutil.h
        not in ../../../src/mesa/glapi/X11/extensions/extutil.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/extutil.h
        not in /usr/include/drm/X11/extensions/extutil.h
        not in /usr/X11R6/include/X11/extensions/extutil.h
        not in /usr/include/X11/extensions/extutil.h
makedepend: warning:  glxextensions.c, line 32: cannot find include file "X11/extensions/extutil.h"
        not in ./X11/extensions/extutil.h
        not in ../../../include/X11/extensions/extutil.h
        not in ../../../include/GL/internal/X11/extensions/extutil.h
        not in ../../../src/mesa/main/X11/extensions/extutil.h
        not in ../../../src/mesa/glapi/X11/extensions/extutil.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/extutil.h
        not in /usr/include/drm/X11/extensions/extutil.h
        not in /usr/X11R6/include/X11/extensions/extutil.h
        not in /usr/include/X11/extensions/extutil.h
makedepend: warning:  glxextensions.c, line 33: cannot find include file "X11/extensions/Xext.h"
        not in ./X11/extensions/Xext.h
        not in ../../../include/X11/extensions/Xext.h
        not in ../../../include/GL/internal/X11/extensions/Xext.h
        not in ../../../src/mesa/main/X11/extensions/Xext.h
        not in ../../../src/mesa/glapi/X11/extensions/Xext.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/Xext.h
        not in /usr/include/drm/X11/extensions/Xext.h
        not in /usr/X11R6/include/X11/extensions/Xext.h
        not in /usr/include/X11/extensions/Xext.h
makedepend: warning:  indirect.c, line 36: cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in ../../../src/mesa/drivers/dri/common/GL/glxproto.h
        not in /usr/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_array.c, line 32: cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in ../../../src/mesa/drivers/dri/common/GL/glxproto.h
        not in /usr/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_array.c (reading indirect_va_private.h, line 39): cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in ../../../src/mesa/drivers/dri/common/GL/glxproto.h
        not in /usr/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  indirect_vertex_program.c, line 31: cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in ../../../src/mesa/drivers/dri/common/GL/glxproto.h
        not in /usr/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  singlepix.c, line 43: cannot find include file "GL/glxproto.h"
        not in ./GL/glxproto.h
        not in ../../../include/GL/glxproto.h
        not in ../../../include/GL/internal/GL/glxproto.h
        not in ../../../src/mesa/main/GL/glxproto.h
        not in ../../../src/mesa/glapi/GL/glxproto.h
        not in ../../../src/mesa/drivers/dri/common/GL/glxproto.h
        not in /usr/include/drm/GL/glxproto.h
        not in /usr/X11R6/include/GL/glxproto.h
        not in /usr/include/GL/glxproto.h
makedepend: warning:  glx_pbuffer.c, line 34: cannot find include file "X11/extensions/extutil.h"
        not in ./X11/extensions/extutil.h
        not in ../../../include/X11/extensions/extutil.h
        not in ../../../include/GL/internal/X11/extensions/extutil.h
        not in ../../../src/mesa/main/X11/extensions/extutil.h
        not in ../../../src/mesa/glapi/X11/extensions/extutil.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/extutil.h
        not in /usr/include/drm/X11/extensions/extutil.h
        not in /usr/X11R6/include/X11/extensions/extutil.h
        not in /usr/include/X11/extensions/extutil.h
makedepend: warning:  glx_pbuffer.c, line 35: cannot find include file "X11/extensions/Xext.h"
        not in ./X11/extensions/Xext.h
        not in ../../../include/X11/extensions/Xext.h
        not in ../../../include/GL/internal/X11/extensions/Xext.h
        not in ../../../src/mesa/main/X11/extensions/Xext.h
        not in ../../../src/mesa/glapi/X11/extensions/Xext.h
        not in ../../../src/mesa/drivers/dri/common/X11/extensions/Xext.h
        not in /usr/include/drm/X11/extensions/Xext.h
        not in /usr/X11R6/include/X11/extensions/Xext.h
        not in /usr/include/X11/extensions/Xext.h
make[3]: Leaving directory `/home/sander/Mesa-6.5.2/src/glx/x11'
make[3]: Entering directory `/home/sander/Mesa-6.5.2/src/glx/x11'
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi -I../../../src/mesa/drivers/dri/common `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/opt/mesa652/\" glcontextmodes.c -o glcontextmodes.o
glcontextmodes.c:45:20: error: X11/X.h: No such file or directory
In file included from glcontextmodes.c:46:
../../../include/GL/glx.h:38:22: error: X11/Xlib.h: No such file or directory
../../../include/GL/glx.h:39:23: error: X11/Xutil.h: No such file or directory
In file included from glcontextmodes.c:46:
../../../include/GL/glx.h:179: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPixmap’
../../../include/GL/glx.h:180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXDrawable’
../../../include/GL/glx.h:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXFBConfigID’
../../../include/GL/glx.h:184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXContextID’
../../../include/GL/glx.h:185: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXWindow’
../../../include/GL/glx.h:186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPbuffer’
../../../include/GL/glx.h:190: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:193: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:196: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXMakeCurrent’
../../../include/GL/glx.h:201: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:204: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:206: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateGLXPixmap’
../../../include/GL/glx.h:209: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:211: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryExtension’
../../../include/GL/glx.h:213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryVersion’
../../../include/GL/glx.h:215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXIsDirect’
../../../include/GL/glx.h:217: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:222: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetCurrentDrawable’
../../../include/GL/glx.h:228: error: expected ‘)’ before ‘font’
../../../include/GL/glx.h:233: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:235: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:237: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:241: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:245: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:248: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:251: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateWindow’
../../../include/GL/glx.h:260: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:262: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreatePixmap’
../../../include/GL/glx.h:265: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:267: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreatePbuffer’
../../../include/GL/glx.h:270: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:272: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:275: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:279: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXMakeContextCurrent’
../../../include/GL/glx.h:282: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetCurrentReadDrawable’
../../../include/GL/glx.h:284: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:287: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:290: error: expected ‘)’ before ‘*’ token
In file included from ../../../include/GL/glx.h:300,
                 from glcontextmodes.c:46:
../../../include/GL/glxext.h:318: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXVideoSourceSGIX’
../../../include/GL/glxext.h:322: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXFBConfigIDSGIX’
../../../include/GL/glxext.h:327: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPbufferSGIX’
../../../include/GL/glxext.h:331: error: expected specifier-qualifier-list before ‘Bool’
../../../include/GL/glxext.h:474: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:474: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:475: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:475: warning: type defaults to ‘int’ in declaration of ‘GLXDrawable’
../../../include/GL/glxext.h:475: error: ‘GLXDrawable’ declared as function returning a function
../../../include/GL/glxext.h:503: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glxext.h:504: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:505: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:505: warning: type defaults to ‘int’ in declaration of ‘GLXContextID’
../../../include/GL/glxext.h:505: error: ‘GLXContextID’ declared as function returning a function
../../../include/GL/glxext.h:506: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:507: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:520: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:521: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:522: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:522: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:523: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:524: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glxext.h:525: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:537: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:537: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:538: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:539: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:540: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:541: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:549: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:561: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:562: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:563: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:564: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:565: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:583: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:592: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:593: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:593: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:601: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:601: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:609: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:617: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:617: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:625: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:625: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:633: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:633: warning: type defaults to ‘int’ in declaration of ‘Bool’
../../../include/GL/glxext.h:633: error: ‘Bool’ declared as function returning a function
../../../include/GL/glxext.h:653: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:654: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:655: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:656: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:657: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:701: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:702: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:703: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:704: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:705: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:706: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:707: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:708: error: expected ‘)’ before ‘*’ token
In file included from glcontextmodes.c:46:
../../../include/GL/glx.h:347: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:348: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:349: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:350: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:351: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:352: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:364: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:365: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:366: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:389: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:390: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:391: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:392: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:394: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:395: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:396: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:397: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:465: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:466: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:481: error: field ‘send_event’ declared as a function
../../../include/GL/glx.h:482: error: expected specifier-qualifier-list before ‘Display’
glcontextmodes.c:47:24: error: GL/glxint.h: No such file or directory
glcontextmodes.c:56:27: error: X11/Xlibint.h: No such file or directory
In file included from glcontextmodes.c:63:
../../../src/mesa/drivers/dri/common/glcontextmodes.h:39: warning: type defaults to ‘int’ in declaration of ‘__GLXvisualConfig’
../../../src/mesa/drivers/dri/common/glcontextmodes.h:39: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
glcontextmodes.c: In function ‘_gl_convert_to_x_visual_type’:
glcontextmodes.c:102: error: ‘TrueColor’ undeclared (first use in this function)
glcontextmodes.c:102: error: (Each undeclared identifier is reported only once
glcontextmodes.c:102: error: for each function it appears in.)
glcontextmodes.c:102: error: ‘DirectColor’ undeclared (first use in this function)
glcontextmodes.c:103: error: ‘PseudoColor’ undeclared (first use in this function)
glcontextmodes.c:103: error: ‘StaticColor’ undeclared (first use in this function)
glcontextmodes.c:104: error: ‘GrayScale’ undeclared (first use in this function)
glcontextmodes.c:104: error: ‘StaticGray’ undeclared (first use in this function)
glcontextmodes.c: At top level:
glcontextmodes.c:128: warning: type defaults to ‘int’ in declaration of ‘__GLXvisualConfig’
glcontextmodes.c:128: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
glcontextmodes.c: In function ‘_gl_context_modes_create’:
glcontextmodes.c:390: warning: implicit declaration of function ‘Xmalloc’
glcontextmodes.c:397: warning: implicit declaration of function ‘memset’
glcontextmodes.c:397: warning: incompatible implicit declaration of built-in function ‘memset’
glcontextmodes.c: In function ‘_gl_context_modes_destroy’:
glcontextmodes.c:436: warning: implicit declaration of function ‘Xfree’
make[3]: *** [glcontextmodes.o] Error 1
make[3]: Leaving directory `/home/sander/Mesa-6.5.2/src/glx/x11'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/sander/Mesa-6.5.2/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/sander/Mesa-6.5.2'
make: *** [linux-dri-x86] Error 2

```

---

### Post by zgornel on 2006-12-17
Ok. I'm going to give you a list of packages, this should reduce the number of errors. Install them with synaptic (some of them might be already installed): ```
libgl1-mesa-dev, libx11-dev, libxrandr-dev, libxt-dev, libxxf86misc-dev, libxxf86vm-dev, x11proto-core-dev, x11proto-gl-dev, x11proto-xf86dri-dev, libdrm-dev, libgl1-mesa-dev, libglib1.2-dev, libglib2.0-dev, libglu1-mesa-dev, libxft-dev, mesa-common-dev, x11proto-gl-dev
```. 

To find them, search with synaptic "gl dev" and "x11 dev". Scroll through the finded packages. After installing the files post the result of the compilation.

---

### Post by Snader on 2006-12-17
How do you know all this?! You amaze me... :)

I thought I knew a little bit about computers, DOS, Windows, software, websites (HTML & CSS), C++, etc. I'm using Linux for about a week now and I feel like I know ab-so-lute-ly nothing of computers! :lol: Especially when it comes to Linux-structure, commands and compiling/installing. I guess it will take a very long time, before I have mastered the basics of Linux. ;)

Anyway, back to the point! It was clearly installing for a longer time than the previous time. Still a number of errors appeared. How do you know which headers to install, when looking at these commandlines in the terminal?

```
GN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM x86/sse_xform3.S -o x86/sse_xform3.o
gcc -c -I../../include -I../../src/mesa -I../../src/mesa/main -I../../src/mesa/glapi -I../../src/mesa/math -I../../src/mesa/tnl -I../../src/mesa/shader -I../../src/mesa/shader/grammar -I../../src/mesa/shader/slang -I../../src/mesa/shader/slang/OSDependent/Linux -I../../src/mesa/shader/slang/OGLCompilersDLL -I../../src/mesa/swrast -I../../src/mesa/swrast_setup -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM x86/sse_xform4.S -o x86/sse_xform4.o
gcc -c -I../../include -I../../src/mesa -I../../src/mesa/main -I../../src/mesa/glapi -I../../src/mesa/math -I../../src/mesa/tnl -I../../src/mesa/shader -I../../src/mesa/shader/grammar -I../../src/mesa/shader/slang -I../../src/mesa/shader/slang/OSDependent/Linux -I../../src/mesa/shader/slang/OGLCompilersDLL -I../../src/mesa/swrast -I../../src/mesa/swrast_setup -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM x86/sse_normal.S -o x86/sse_normal.o
gcc -c -I../../include -I../../src/mesa -I../../src/mesa/main -I../../src/mesa/glapi -I../../src/mesa/math -I../../src/mesa/tnl -I../../src/mesa/shader -I../../src/mesa/shader/grammar -I../../src/mesa/shader/slang -I../../src/mesa/shader/slang/OSDependent/Linux -I../../src/mesa/shader/slang/OGLCompilersDLL -I../../src/mesa/swrast -I../../src/mesa/swrast_setup -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM x86/read_rgba_span_x86.S -o x86/read_rgba_span_x86.o
gcc -c -I../../include -I../../src/mesa -I../../src/mesa/main -I../../src/mesa/glapi -I../../src/mesa/math -I../../src/mesa/tnl -I../../src/mesa/shader -I../../src/mesa/shader/grammar -I../../src/mesa/shader/slang -I../../src/mesa/shader/slang/OSDependent/Linux -I../../src/mesa/shader/slang/OGLCompilersDLL -I../../src/mesa/swrast -I../../src/mesa/swrast_setup -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM tnl/t_vtx_x86_gcc.S -o tnl/t_vtx_x86_gcc.o
mklib: Making Linux static library:  libmesa.a
ar: creating libmesa.a
cd drivers/dri ; make
make[5]: Entering directory `/home/sander/Mesa-6.5.2/src/mesa/drivers/dri'
echo savage
savage
savage
make[6]: Entering directory `/home/sander/Mesa-6.5.2/src/mesa/drivers/dri/savage'
../Makefile.template:110: depend: No such file or directory
touch depend
makedepend -fdepend  -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  ../../common/driverfuncs.c ../common/utils.c ../common/texmem.c ../common/vblank.c ../common/dri_util.c ../common/xmlconfig.c ../common/drirenderbuffer.c  savage_xmesa.c savagedd.c savagestate.c savagetex.c savagetris.c savagerender.c savageioctl.c savagespan.c  \
                 2>&1 /dev/null
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/bits/types.h, line 31): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/limits.h, line 125): cannot find include file "limits.h"
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/stdlib.h, line 33): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/sys/types.h, line 147): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/alloca.h, line 25): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/stdio.h, line 34): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/_G_config.h, line 14): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/wchar.h, line 48): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/gconv.h, line 31): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/libio.h, line 53): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../../../src/mesa/drivers/dri/common/stdarg.h
        not in server/stdarg.h
        not in ../../../../../include/stdarg.h
        not in ../../../../../include/GL/internal/stdarg.h
        not in ../../../../../src/mesa/stdarg.h
        not in ../../../../../src/mesa/main/stdarg.h
        not in ../../../../../src/mesa/glapi/stdarg.h
        not in ../../../../../src/mesa/math/stdarg.h
        not in ../../../../../src/mesa/transform/stdarg.h
        not in ../../../../../src/mesa/shader/stdarg.h
        not in ../../../../../src/mesa/swrast/stdarg.h
        not in ../../../../../src/mesa/swrast_setup/stdarg.h
        not in ../../../../../src/egl/main/stdarg.h
        not in ../../../../../src/egl/drivers/dri/stdarg.h
        not in /usr/include/drm/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/string.h, line 33): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading ../../../../../src/mesa/main/glheader.h, line 72): cannot find include file "float.h"
        not in ./float.h
        not in ../../../../../src/mesa/drivers/dri/common/float.h
        not in server/float.h
        not in ../../../../../include/float.h
        not in ../../../../../include/GL/internal/float.h
        not in ../../../../../src/mesa/float.h
        not in ../../../../../src/mesa/main/float.h
        not in ../../../../../src/mesa/glapi/float.h
        not in ../../../../../src/mesa/math/float.h
        not in ../../../../../src/mesa/transform/float.h
        not in ../../../../../src/mesa/shader/float.h
        not in ../../../../../src/mesa/swrast/float.h
        not in ../../../../../src/mesa/swrast_setup/float.h
        not in ../../../../../src/egl/main/float.h
        not in ../../../../../src/egl/drivers/dri/float.h
        not in /usr/include/drm/float.h
        not in /usr/include/float.h
makedepend: warning:  ../../common/driverfuncs.c (reading ../../../../../src/mesa/main/glheader.h, line 73): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../../../src/mesa/drivers/dri/common/stdarg.h
        not in server/stdarg.h
        not in ../../../../../include/stdarg.h
        not in ../../../../../include/GL/internal/stdarg.h
        not in ../../../../../src/mesa/stdarg.h
        not in ../../../../../src/mesa/main/stdarg.h
        not in ../../../../../src/mesa/glapi/stdarg.h
        not in ../../../../../src/mesa/math/stdarg.h
        not in ../../../../../src/mesa/transform/stdarg.h
        not in ../../../../../src/mesa/shader/stdarg.h
        not in ../../../../../src/mesa/swrast/stdarg.h
        not in ../../../../../src/mesa/swrast_setup/stdarg.h
        not in ../../../../../src/egl/main/stdarg.h
        not in ../../../../../src/egl/drivers/dri/stdarg.h
        not in /usr/include/drm/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  ../../common/driverfuncs.c (reading /usr/include/inttypes.h, line 38): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../../common/driverfuncs.c (reading ../../../../../include/GL/glext.h, line 3128): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../common/utils.c (reading /usr/include/drm/drm.h), line 196: # warning "__SIZE_TYPE__ not defined.  Assuming sizeof(size_t) == sizeof(unsigned long)!"
makedepend: warning:  ../common/vblank.c (reading /usr/include/unistd.h, line 195): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  ../common/dri_util.c, line 20: cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../../../src/mesa/drivers/dri/common/stdarg.h
        not in server/stdarg.h
        not in ../../../../../include/stdarg.h
        not in ../../../../../include/GL/internal/stdarg.h
        not in ../../../../../src/mesa/stdarg.h
        not in ../../../../../src/mesa/main/stdarg.h
        not in ../../../../../src/mesa/glapi/stdarg.h
        not in ../../../../../src/mesa/math/stdarg.h
        not in ../../../../../src/mesa/transform/stdarg.h
        not in ../../../../../src/mesa/shader/stdarg.h
        not in ../../../../../src/mesa/swrast/stdarg.h
        not in ../../../../../src/mesa/swrast_setup/stdarg.h
        not in ../../../../../src/egl/main/stdarg.h
        not in ../../../../../src/egl/drivers/dri/stdarg.h
        not in /usr/include/drm/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  ../common/dri_util.c (reading /usr/include/sys/mman.h, line 26): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  savage_xmesa.c (reading /usr/include/X11/Xlib.h, line 75): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  savage_xmesa.c (reading /usr/include/X11/Xlibint.h, line 346): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../../../src/mesa/drivers/dri/common/stddef.h
        not in server/stddef.h
        not in ../../../../../include/stddef.h
        not in ../../../../../include/GL/internal/stddef.h
        not in ../../../../../src/mesa/stddef.h
        not in ../../../../../src/mesa/main/stddef.h
        not in ../../../../../src/mesa/glapi/stddef.h
        not in ../../../../../src/mesa/math/stddef.h
        not in ../../../../../src/mesa/transform/stddef.h
        not in ../../../../../src/mesa/shader/stddef.h
        not in ../../../../../src/mesa/swrast/stddef.h
        not in ../../../../../src/mesa/swrast_setup/stddef.h
        not in ../../../../../src/egl/main/stddef.h
        not in ../../../../../src/egl/drivers/dri/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/include/stddef.h
make[6]: Leaving directory `/home/sander/Mesa-6.5.2/src/mesa/drivers/dri/savage'
make[6]: Entering directory `/home/sander/Mesa-6.5.2/src/mesa/drivers/dri/savage'
gcc -c -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM  ../../common/driverfuncs.c -o ../../common/driverfuncs.o
gcc -c -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM  ../common/utils.c -o ../common/utils.o
gcc -c -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM  ../common/texmem.c -o ../common/texmem.o
gcc -c -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM  ../common/vblank.c -o ../common/vblank.o
../common/vblank.c: In function ‘driGetCurrentVBlank’:
../common/vblank.c:306: error: ‘DRM_VBLANK_SECONDARY’ undeclared (first use in this function)
../common/vblank.c:306: error: (Each undeclared identifier is reported only once
../common/vblank.c:306: error: for each function it appears in.)
../common/vblank.c: In function ‘driWaitForVBlank’:
../common/vblank.c:363: error: ‘DRM_VBLANK_SECONDARY’ undeclared (first use in this function)
make[6]: *** [../common/vblank.o] Error 1
make[6]: Leaving directory `/home/sander/Mesa-6.5.2/src/mesa/drivers/dri/savage'
make[5]: *** [subdirs] Error 1
make[5]: Leaving directory `/home/sander/Mesa-6.5.2/src/mesa/drivers/dri'
make[4]: *** [linux-solo] Error 2
make[4]: Leaving directory `/home/sander/Mesa-6.5.2/src/mesa'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/home/sander/Mesa-6.5.2/src/mesa'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/sander/Mesa-6.5.2/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/sander/Mesa-6.5.2'
make: *** [linux-dri-x86] Error 2

```

---

### Post by zgornel on 2006-12-17
To get an ideea about how to scoop out dependencies, look at the output of the compilation. For example, taking the first compile results, notice this line: ```
glcontextmodes.c:47:24: error: GL/glxint.h: No such file or directory
``` This means that while compiling glcontextmodes.c, the compiler did not found glxint.h. You google the file and come up with the package that contains it. In this case I think it was libgl1-mesa-dev.
Continuing, among the last lines you can see the "gcc -c -I .....". Those are compilation instructions, their result is a .o file (might be driver, library etc.). The last gcc line before the errors ended up with "../common/vblank.c -o ../common/vblank.o". This is the module that it cannot create. As seen below the line, "../common/vblank.c:363: error: &#8216;DRM_VBLANK_SECONDARY&#8217; undeclared (first use in this function)". This means that in vblank.c there is a function that has no definition whatsoever.
Most of the text reffers to some other .h files that are not found. stddef.h is part of the kernel headers and it is pretty important. Check and see if you have the build-essential and kernel-headers packages installed. If not install it and retry the compillation, you're close :mrgreen: .

P.S. The build-essential package will actually install gcc, headers and dev packages needed for basic compillations. You already installed gcc 3.4, I think that it will upgrade it to 4.1 but I am not sure.
In my case, the installation of Mesa was a trial and error process, it took about 2 days before I managed to install it. It did not help me much but it might help you :D.

---

### Post by martinkaethler on 2006-12-18
When and if you work it all out... could you post the list of dependencies that you needed to get to make your S3 graphics card to work. Thanks!

---

### Post by Snader on 2006-12-18
Sure. I will. :)

---

### Post by martinkaethler on 2006-12-18
i'm just dying here trying to figure this graphics card out... i'm running an old HP Pavillion zt1170. Got it for free from a friend because it was too slow for XP... but not for Linux!

I'm stuck at the compiling Mesa 6.5.2

I can't seem to figure the issues out... and my terminal goes too far, so it doesn't let me copy the whole error set...

Anyway, keep fighting the good fight and let us no0bs know what is going on :D

---

### Post by Snader on 2006-12-18
*** SOLUTION TO THE PROBLEM ***

Yesterday I gave up. I quit installing all those packages, reinstalled Ubuntu and gave it a fresh start. Couldn't find an answer anywhere. But, with some logical thinking, I managed to solve the problem! :)

By default, Ubuntu Edgy Eft has everything(!) to support the savage videocard with Direct-rendering. The latest versions of libdrm, mesa and the savage-driver are already there! So, why install them again?

Opened my xorg.conf, searched the section "Device" and changed the driver to "savage" (instead of "via"). The result looks like this:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"savage"
	BusID		"PCI:1:0:0"
```

Second, I looked up the xorg.0.log file and found this:
```
(II) SAVAGE(0): 9348 kB of Videoram needed for 3D; 8192 kB of Videoram available
(EE) SAVAGE(0): Insufficient Videoram available for 3D -- Try a lower color depth or smaller desktop.  For integrated savages try increasing the videoram in the BIOS.
(EE) SAVAGE(0): DRI isn't enabled
```
Veeery interesting, isn't it? ;)

Opened my xorg.conf again, searched the section Screen" and changed the DefaultDepth to "16" (instead of "24"). The result looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
```

Did a reboot and everything worked fine! :D 



Additional Information:
xorg.0.log said:
```
(II) SAVAGE(0): 4740 kB of Videoram needed for 3D; 8192 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
```

"glxinfo |grep direct" said:
```
libGL warning: 3D driver claims to not support visual 0x42
direct rendering: Yes
```

"glxgears -printfps" said:
```
959 frames in 5.0 seconds = 191.596 FPS
809 frames in 5.0 seconds = 161.761 FPS
865 frames in 5.0 seconds = 172.878 FPS
867 frames in 5.0 seconds = 173.275 FPS
862 frames in 5.0 seconds = 172.377 FPS
```

And last, but not least. Tux Racer runs veeery smooth now. :lol:

---

### Post by martinkaethler on 2006-12-18
This is great! Good job,

 alas... I can't seem to get my screen to anything higher than 800x600 and it is a laptop... so it looks like there is a huge black frame around my desktop.... and it is all.. so... big and unuse-able!

---

### Post by martinkaethler on 2006-12-18
OooooooH Yes!


  I figured it out. I just ran:

dpkg-reconfigure xserver-xorg

  And made sure all the settings made sense for my laptop. It is all about the range of frequencies.

Peace everybody!

---

### Post by Snader on 2006-12-22
Hi there, I've found out something new. :) I've been thinking about this quote I read in the log file: "For integrated savages try increasing the videoram in the BIOS."

The Twister I have, does not have any dedicated Video memory, it shares the main system memory. The amount that is allocated can be configured in the BIOS under System Device Menu and set the VGA frame Buffer Size to 8, 16 or 32MB as required.

So I increased the "VGA frame buffer size" from 8 Mb to 32 Mb. This strongly enhances the performance of the videocard! Watch the results of the "glxgears -printfps":
```
1667 frames in 5.0 seconds = 333.384 FPS
1838 frames in 5.0 seconds = 367.478 FPS
1836 frames in 5.0 seconds = 367.094 FPS
1835 frames in 5.0 seconds = 366.991 FPS
1724 frames in 5.0 seconds = 344.622 FPS
```

Everything runs even mooore smooth now. :D The results are quite fabulous!

---

### Post by rctxtreme on 2006-12-30
This is strange.

The test comes up at around 350fps, yet with games such as [Jumper Two](http://www.helixgamesinc.com) on wine, Ogmo is randomly normal speed and matrix-slow.

YouTube was also horridly slow.

These commands when tried were said to be not found however ALL repos are enabled in Synaptic...
> sudo apt-get install linux-image-2.6.12-10-k7
sudo apt-get install linux-headers-2.6.12-10-k7
sudo apt-get install linux-restricted-modules-2.6.12-10-k7

Also, this information when read, I checked that driver "savage" was in the list section "device".
> Have you tried putting in /etc/X11/xorg.conf , in Section "Device", Driver "savage" ?

(edgy)

---

### Post by Snader on 2007-01-02
I'm afraid I cannot help you on this problem. My experience does not reach any further than the solution I mentioned on page 3.

---

### Post by rctxtreme on 2007-01-02
Your soloution? Well please tell me which app, and where? Not just xorg.conf... (Linux is starting to annoy me :P)

---


---
title: "Installing eViacam onto Ubuntu 9.10 is Not Easy."
date: 2010-02-01
forum: Assistive Technology &amp; Accessibility
---

### Post by Sean Moran on 2010-02-01
A friend of mine has been attempting to install the Linux version of eViacam on his HDX1200 HP laptop running Ubuntu 9.10 for over a week without success.  He is unable to move his arms and hands due to a permanent injury, and uses head movements in conjunction with a web-camera to operate a virtual keyboard and mouse. 

This is why I hope to help, as I do have the ability to use my arms and hands so I hope that I can help get the eViacam system setup more efficiently.  He has already installed the Windows 7 version on the same machine without a problem.  I believe that anything Windows can do, Linux can do better.  This is the other reason why I am most interested in getting this software installed for my friend.

The tar.gz file can be found at the link below:

[http://sourceforge.net/projects/eviacam/](http://sourceforge.net/projects/eviacam/)
 
According the the INSTALL instructions, once the tar.gz file has been extracted to the /usr/local/eviacam-1.2 directory (I hope that's a reasonable place to put the source & installation files), installation is a matter of opening a terminal,

```
 
cd /usr/local/eviacam-1.2, and type 
./configure 
make 
make install

```After installing additional libraries such as libXext and libXtst, I am stumped at the error message produced by the ./configure command:

```

...
checking gdk version... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
not found
configure: error: gtk+-2.0 is required.

```I realise that this would be a lot of work for anyone to help me help my friend to get installed properly, as it is a rather alpha-quality version by the look of it, but it's for the sake of Linux, for Ubuntu, and for a friend who has to make a lot more effort to type commands into a terminal with a virtual keyboard driven by his head movements than I do, could anyone with more understanding of compiling from source code help me to get this eViacam software installed?


---o0o---

Not to worry.  Sorry.  I read the thread from back in June, [http://ubuntuforums.org/showthread.php?t=1123092&highlight=libavcodec0d](http://ubuntuforums.org/showthread.php?t=1123092&highlight=libavcodec0d)

and assume that it might have been unlikely that the eViacam application was ever ported to Ubuntu.  Please reply if you know of any other software that might do the job in Karmic.  My friend tells me he couldn't get Gnome-Mousetrap to work after installing it smoothly, but it might be his webcam.  I have to wait until Friday payday before I can go shopping for a webcam, so I'll try gnome-mousetrap after I have the finances to afford the technology.

---

### Post by GraysonPeddie on 2010-02-01
I found one:

[http://live.gnome.org/MouseTrap/UsingIt](http://live.gnome.org/MouseTrap/UsingIt)

This is MouseTrap for GNOME.

Update: When I ```
apt-get install mousetrap
``` and run ```
mousetrap
``` in a terminal, I get this:

```
*** buffer overflow detected ***: mousetrap terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x3b0de8]
/lib/tls/i686/cmov/libc.so.6[0x3afe20]
/lib/tls/i686/cmov/libc.so.6[0x3af558]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x33959e]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x60a)[0x30d14a]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x3af60d]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x3af54d]
mousetrap[0x804b919]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x2e6b56]
mousetrap(__gxx_personality_v0+0x5d)[0x8049211]
======= Memory map: ========
00110000-00134000 r-xp 00000000 08:02 3362       /lib/tls/i686/cmov/libm-2.10.1.so
00134000-00135000 r--p 00023000 08:02 3362       /lib/tls/i686/cmov/libm-2.10.1.so
00135000-00136000 rw-p 00024000 08:02 3362       /lib/tls/i686/cmov/libm-2.10.1.so
00136000-00184000 r-xp 00000000 08:02 31491      /usr/lib/libmikmod.so.2.0.4
00184000-00185000 r--p 0004e000 08:02 31491      /usr/lib/libmikmod.so.2.0.4
00185000-00186000 rw-p 0004f000 08:02 31491      /usr/lib/libmikmod.so.2.0.4
00186000-00187000 rw-p 00000000 00:00 0 
00187000-00249000 r-xp 00000000 08:02 8035       /usr/lib/libasound.so.2.0.0
00249000-0024d000 r--p 000c1000 08:02 8035       /usr/lib/libasound.so.2.0.0
0024d000-0024e000 rw-p 000c5000 08:02 8035       /usr/lib/libasound.so.2.0.0
0024e000-00253000 r-xp 00000000 08:02 8300       /usr/lib/libogg.so.0.6.0
00253000-00254000 r--p 00004000 08:02 8300       /usr/lib/libogg.so.0.6.0
00254000-00255000 rw-p 00005000 08:02 8300       /usr/lib/libogg.so.0.6.0
00255000-00268000 r-xp 00000000 08:02 31526      /usr/lib/libSDL_gfx.so.13.5.1
00268000-00269000 r--p 00013000 08:02 31526      /usr/lib/libSDL_gfx.so.13.5.1
00269000-0026a000 rw-p 00014000 08:02 31526      /usr/lib/libSDL_gfx.so.13.5.1
0026a000-0026b000 rw-p 00000000 00:00 0 
0026b000-00273000 r-xp 00000000 08:02 7968       /usr/lib/libfusion-1.2.so.0.7.0
00273000-00274000 r--p 00007000 08:02 7968       /usr/lib/libfusion-1.2.so.0.7.0
00274000-00275000 rw-p 00008000 08:02 7968       /usr/lib/libfusion-1.2.so.0.7.0
00275000-0027c000 r-xp 00000000 08:02 3374       /lib/tls/i686/cmov/librt-2.10.1.so
0027c000-0027d000 r--p 00006000 08:02 3374       /lib/tls/i686/cmov/librt-2.10.1.so
0027d000-0027e000 rw-p 00007000 08:02 3374       /lib/tls/i686/cmov/librt-2.10.1.so
0027e000-0029a000 r-xp 00000000 08:02 6620       /usr/lib/libxcb.so.1.1.0
0029a000-0029b000 r--p 0001c000 08:02 6620       /usr/lib/libxcb.so.1.1.0
0029b000-0029c000 rw-p 0001d000 08:02 6620       /usr/lib/libxcb.so.1.1.0
0029c000-0029e000 r-xp 00000000 08:02 6616       /usr/lib/libXau.so.6.0.0
0029e000-0029f000 r--p 00001000 08:02 6616       /usr/lib/libXau.so.6.0.0
0029f000-002a0000 rw-p 00002000 08:02 6616       /usr/lib/libXau.so.6.0.0
002a0000-002ae000 r-xp 00000000 08:02 6634       /usr/lib/libXext.so.6.4.0
002ae000-002af000 r--p 0000d000 08:02 6634       /usr/lib/libXext.so.6.4.0
002af000-002b0000 rw-p 0000e000 08:02 6634       /usr/lib/libXext.so.6.4.0
002b0000-002b8000 r-xp 00000000 08:02 7978       /usr/lib/libXrender.so.1.3.0
002b8000-002b9000 r--p 00007000 08:02 7978       /usr/lib/libXrender.so.1.3.0
002b9000-002ba000 rw-p 00008000 08:02 7978       /usr/lib/libXrender.so.1.3.0
002d0000-0040e000 r-xp 00000000 08:02 3358       /lib/tls/i686/cmov/libc-2.10.1.so
0040e000-00410000 r--p 0013e000 08:02 3358       /lib/tls/i686/cmov/libc-2.10.1.so
00410000-00411000 rw-p 00140000 08:02 3358       /lib/tls/i686/cmov/libc-2.10.1.so
00411000-00414000 rw-p 00000000 00:00 0 
00500000-0051a000 r-xp 00000000 08:02 12259      /usr/lib/libvorbis.so.0.4.0
0051a000-0051b000 r--p 00019000 08:02 12259      /usr/lib/libvorbis.so.0.4.0
0051b000-00529000 rw-p 0001a000 08:02 12259      /usr/lib/libvorbis.so.0.4.0
00585000-0066b000 r-xp 00000000 08:02 936        /usr/lib/libstdc++.so.6.0.13
0066b000-0066f000 r--p 000e6000 08:02 936        /usr/lib/libstdc++.so.6.0.13
0066f000-00670000 rw-p 000ea000 08:02 936        /usr/lib/libstdc++.so.6.0.13
00670000-00677000 rw-p 00000000 00:00 0 
00677000-007a1000 r-xp 00000000 08:02 6622       /usr/lib/libX11.so.6.2.0
007a1000-007a2000 ---p 0012a000 08:02 6622       /usr/lib/libX11.so.6.2.0
007a2000-007a3000 r--p 0012a000 08:02 6622       /usr/lib/libX11.so.6.2.0
007a3000-007a5000 rw-p 0012b000 08:02 6622       /usr/lib/libX11.so.6.2.0
007a5000-007a6000 rw-p 00000000 00:00 0 
007ce000-007d2000 r-xp 00000000 08:02 6141       /usr/lib/libXfixes.so.3.1.0
007d2000-007d3000 r--p 00003000 08:02 6141       /usr/lib/libXfixes.so.3.1.0
007d3000-007d4000 rw-p 00004000 08:02 6141       /usr/lib/libXfixes.so.3.1.0
00821000-00848000 r-xp 00000000 08:02 31542      /usr/lib/libSDL_mixer-1.2.so.0.2.6
00848000-00849000 r--p 00026000 08:02 31542      /usr/lib/libSDL_mixer-1.2.so.0.2.6
00849000-00852000 rw-p 00027000 08:02 31542      /usr/lib/libSDL_mixer-1.2.so.0.2.6
00852000-0087c000 rw-p 00000000 00:00 0 
00944000-009ba000 r-xp 00000000 08:02 7967       /usr/lib/libdirectfb-1.2.so.0.7.0
009ba000-009bb000 ---p 00076000 08:02 7967       /usr/lib/libdirectfb-1.2.so.0.7.0
009bb000-009bc000 r--p 00076000 08:02 7967       /usr/lib/libdirectfb-1.2.so.0.7.0
009bc000-009bd000 rw-p 00077000 08:02 7967       /usr/lib/libdirectfb-1.2.so.0.7.0
009bd000-009be000 rw-p 00000000 00:00 0 
009c5000-009ce000 r-xp 00000000 08:02 8011       /usr/lib/libXcursor.so.1.0.2
009ce000-009cf000 r--p 00008000 08:02 8011       /usr/lib/libXcursor.so.1.0.2
009cf000-009d0000 rw-p 00009000 08:02 8011       /usr/lib/libXcursor.so.1.0.2
009e1000-00a1c000 r-xp 00000000 08:02 31540      /usr/lib/libsmpeg-0.4.so.0.1.4
00a1c000-00a1d000 r--p 0003a000 08:02 31540      /usr/lib/libsmpeg-0.4.so.0.1.4
00a1d000-00a1e000 rw-p 0003b000 08:02 31540      /usr/lib/libsmpeg-0.4.so.0.1.4
00a1e000-00a3a000 rw-p 00000000 00:00 0 
00b08000-00b23000 r-xp 00000000 08:02 517        /lib/ld-2.10.1.so
00b23000-00b24000 r--p 0001a000 08:02 517        /lib/ld-2.10.1.so
00b24000-00b25000 rw-p 0001b000 08:02 517        /lib/ld-2.10.1.so
00b55000-00b57000 r-xp 00000000 08:02 3361       /lib/tls/i686/cmov/libdl-2.10.1.so
00b57000-00b58000 r--p 00001000 08:02 3361       /lib/tls/i686/cmov/libdl-2.10.1.so
00b58000-00b59000 rw-p 00002000 08:02 3361       /lib/tls/i686/cmov/libdl-2.10.1.so
00c3b000-00c3f000 r-xp 00000000 08:02 6618       /usr/lib/libXdmcp.so.6.0.0
00c3f000-00c40000 rw-p 00003000 08:02 6618       /usr/lib/libXdmcp.so.6.0.0
00c45000-00c46000 r-xp 00000000 00:00 0          [vdso]
00cfd000-00d12000 r-xp 00000000 08:02 3372       /lib/tls/i686/cmov/libpthread-2.10.1.so
00d12000-00d13000 r--p 00014000 08:02 3372       /lib/tls/i686/cmov/libpthread-2.10.1.so
00d13000-00d14000 rw-p 00015000 08:02 3372       /lib/tls/i686/cmov/libpthread-2.10.1.soAborted
```

Update 2: Forgot to add: Ubuntu 9.10 is running in my Acer Aspire One AOA150 with a built-in webcam.

---

### Post by Sean Moran on 2010-02-02
Thank you so much.  I have passed that link for using mousetrap onto my friend and will hopefully have the required web cam to try it out myself on Friday.  It might be best to try to accord with the software that Ubuntu recommends.  I was not aware of the required terminal commands ./mousetrap et al, so maybe this will solve the problem adequately.

---

### Post by cmauri on 2010-02-02
I've successfully compiled and run eViacam on an almost clean Ubuntu 9.10 (karmic) x86_64. The problem was that you hadn't installed the required development libraries. Unfortunately, there is no easy way to generate executables for all Linux flavours and so sometimes a "manual" compilation is required (which is usually somewhat painful).

First of all install the required libraries. Run the following commands:

sudo apt-get install libxext-dev
sudo apt-get install libxtst-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libwxbase2.8-dev
sudo apt-get install libwxgtk2.8-dev
sudo apt-get install libhighgui-dev
sudo apt-get install libswscale-dev

Then, you need to modify two files to correct a bug (the fix will be included in the next release):

creavision/crvcamera_cv.cpp
creavision/crvcamera_cv.h

Change g_deviceNames[MAX_CV_DEVICES][10]; by g_deviceNames[MAX_CV_DEVICES][100];

Check this post for further details: 
[https://sourceforge.net/projects/eviacam/forums/forum/898005/topic/3522717](https://sourceforge.net/projects/eviacam/forums/forum/898005/topic/3522717)

Then:

./configure
make

If this works properly you may want to generate a .deb package:

make deb

Install it:

sudo dpkg -i debian-build/eviacam_1.2_amd64.deb

Run from the applications menu. Enjoy.

The only drawback is that there are some issues with the Click Window.

--
See the original post:

[https://sourceforge.net/projects/eviacam/forums/forum/898005/topic/3538914/index/page/1](https://sourceforge.net/projects/eviacam/forums/forum/898005/topic/3538914/index/page/1)

---

### Post by GraysonPeddie on 2010-02-03
You can do all of that in one line:

```
sudo apt-get install libxext-dev libxtst-dev libgtk2.0-dev libwxbase2.8-dev libwxgtk2.8-dev libhighgui-dev libswscale-dev
```

---

### Post by Kubunteando on 2010-02-03
Some experience after finally succeeding:

You can check the opencv webcam compatibility here:
[http://opencv.willowgarage.com/wiki/Welcome/OS](http://opencv.willowgarage.com/wiki/Welcome/OS)

Mine (Logitech Quickcam Messager) uses the driver gspca_zc3xx and it is only supported in opencv 2.0. With Karmic by default you only find older versions. So when starting eviacam it will tell that cannot find any camera.

There are karmic repositories having opencv 2.0:
# opencv 2.0
# ppa:gijzelaar/opencv2-karmic
deb [http://ppa.launchpad.net/gijzelaar/opencv2-karmic/ubuntu](http://ppa.launchpad.net/gijzelaar/opencv2-karmic/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/gijzelaar/opencv2-karmic/ubuntu](http://ppa.launchpad.net/gijzelaar/opencv2-karmic/ubuntu) karmic main

On those repositories you find libcv4, libcv-dev and others on version 2.0.
After installing those (you have to uninstall libcv1) and compiling eviacam works fine.

I found the issue that if I install this opencv 2.0 I cannot use "make deb" to create the debian package. It complains that there is an unmet dependency, but I cannot install the package it complains about because it is incompatible with openvc 2.0 packages. Maybe a small bug?

I use Kubuntu and I get also the icon in the taskbar.
Very nice application.

---

### Post by GraysonPeddie on 2010-02-04
Is it possible if you can go into MakeFile by typing:

```
nano MakeFile
```

in the source directory and find the "deb" portion of it? Maybe then you can change the package dependencies there.

---

### Post by cmauri on 2010-02-04
You can edit the build dependencies here:

debian/control

I am not sure why is not working because it depends on libcvaux-dev (>= 1.0), so any latter version of libcvaux-dev should work. 

Anyway, you can try editing this dependency or (better) adding an alternative package using the "|" operator.

For instance:

Build-Depends: debhelper (>= 5), libwxgtk2.6-dev (>= 2.6.3) | libwxgtk2.8-dev, libgtk2.0-dev, libcvaux-dev (>= 1.0) | libcvaux-dev (>= 2.0), libhighgui1 (>= 1.0), libpng12-dev, libxtst-dev, libxext-dev

Let me know whether it worked to include the fix in the next release.

---

### Post by GraysonPeddie on 2010-02-05
That's strange. I thought >= means "greater than or equal to."

---

### Post by Sean Moran on 2010-02-12
Thank you for further instruction and sorry to have been absorbed in getting Mousetrap to run for the past week, and too absorbed in the process to spend much time on forums.  

I see now that eViacam and Mousetrap both seem to require the addition of some -dev libraries, but went with the Mousetrap option because it seems more a part of the Ubuntu distribution and my friend and I are both running the garden variety i386 versions of Ubuntu 9.10 rather than the 64-bit alternative, which does seem to create further complications.

I can only add now that to coincide with the thread title, installing Mousetrap onto Ubuntu 9.10 is not easy either, but I did manage to get a little script file and the required items to get it installed and ~/.config/autostart -ed two days ago.

Although the title might be misleading with regards Mousetrap, the .zip file that should perform the installation and configuration on Ubuntu 9.10 even if you unzip it in the ~/Downloads directory is uploaded at [http://thaibuntu.webatu.com/arc/minitrap.zip](http://thaibuntu.webatu.com/arc/minitrap.zip) and the zipped setup is 4.1Mb.

Below is the script that seems to do the job with the required files in etc/apt/sources.list and etc/skel/bin etc/skel/.config and etc/skel/.mousetrap including the sources list deb entry for Skype because that is how I've been communicating with my friend over the past week.  
```

#! /bin/bash
echo UPDATING APT SOURCES ...
sudo cp /etc/apt/sources.list /etc/apt/sources.pretrap
sudo cp etc/apt/sources.list /etc/apt/sources.list
sudo apt-get update
echo INSTALLING GNOME-COMMON ...
sudo apt-get -y install gnome-common
echo INSTALLING LIBGLIB2.0 ...
sudo apt-get -y install libglib2.0-dev
echo INSTALLING PYTHON2.6-DEV ...
sudo apt-get -y install python2.6-dev
echo INSTALLING PYTHON-XLIB ...
sudo apt-get -y install python-xlib
echo INSTALLING PYTHON-OPENCV ...
sudo apt-get -y install python-opencv
echo COPYING MOUSETRAP FILES TO USER HOME DIRECTORY, INCLUDING AUTOSTART ...
sudo cp -a etc/skel/* ~/
sudo cp -a etc/skel/.* ~/
cd ~/bin/mousetrap
echo MOUSETRAP AUTOGEN.SH ...
sudo ./autogen.sh
echo MOUSETRAP MAKE ...
sudo make
echo MOUSETRAP MAKE INSTALL ...
sudo make install

```

It's quite simple stuff but it works for me and has installed for him, after downloading that 4.1Mb zip file to try it out.

Now though, my friend reports another problem with the operation of the mouse via his webcam related to the movement of the green dot in the rectangle as well as on the camera image in the Mousetrap window.

I have also noticed a similar problem here at my hotel room, and found that control of the mouse cursor using my el-cheapo Nio webcam and Mousetrap is more successful with the door shut and curtains closed or at night, when there seems to be less reflective light to distract Mousetrap from following a consistent green dot on my forehead or eyelid or nose or chin.

Inside the user's ~/.mousetrap directory is a file called userSettings.cfg which reads like this:

```

[gui]
showCapture = True
showMainGui = True
showPointMapper = True

[access]
reqMovement = 10

[cam]
mouseMode = forehead
inputDevIndex = 0
flipImage = False

[main]
debugLevel = 10
algorithm = forehead
startCam = True
addon = 

[mouse]
defClick = b1c
stepSpeed = 5

```

I am in two minds about whether I should start a separate thread with the Mousetrap in the title or append this thread, but seeing it's here and so am I, I'll start from here and wait over the weekend if anyone with the knowledge of Mousetrap might be onbservant and notice it here.  

The requirement now is to find a way that under differing light conditions throughout morning, afternoon and night (his room's windows face eastward but but have curtains that can be drawn), the green dot on the Script Mapper and on the camera image can be set to range across the x-y axes of the screen but not too far beyond, and hopefully start around the centre and stay focussed on the same point of the user's head in the webcam.  

I get the impression that tweaking these settings in the config file might be part of the solution, as well as reducing the sensitivity and acceleration within System -> Preferences -> Mouse through the Ubuntu menu.

Can anyone offer any instructions on how to configure the now installed and autostarting working application of mousetrap?

---

### Post by Sean Moran on 2010-02-22
My friend found a website that linked a repository for eViacam and told me last night.  I tested it out this morning and it worked very nicely.  Significantly better than MouseTrap  IMHO. 

The website would appear to be in Spanish but the directions were quite clear:

[http://lihuen.linti.unlp.edu.ar/index.php/EViacam](http://lihuen.linti.unlp.edu.ar/index.php/EViacam)

1. Add to the /etc/apt/sources.list the following line:

deb [http://repo.lihuen.linti.unlp.edu.ar/lihuen](http://repo.lihuen.linti.unlp.edu.ar/lihuen) lenny/lihuen3 main

2. sudo apt-get update

3. sudo apt-get install eviacam


It seems like a very nice piece of software, after all the uncertainty I've had over all this time with trying to get it to install.

---

### Post by Alex 999 on 2010-02-22
Also a word to Senor Cesar, do you have a repo for the latest version? The one in the Espanol language forum is 1.1 and it would be nice to have the latest one. We are still having never ending dependency problems in Ubuntu. I'm the Quadriplegic that my friend Sean has been helping. 
 
When are you releasing your new one?  Can you design a deb file for Ubuntu? I have given up due to the endless dependency requirements.

Muchas Gracias!

---

### Post by cmauri on 2010-02-23
Currently the only official repository is that one you can reach through the official website [1], that is, the files available at SF.net. There I try to put several pre-compiled binaries for Windows and for some Linux distros along with the sources. Obviously, as I only have few Linux distros installed on my computer, I can only produce binaries for these systems (may be there is a way, but I don't know).

I plan to launch a minor revision soon, probably the next week. Taking into account the popularity of Ubuntu I will probably add the binaries for this platform also. But, I think that the real solution is that somebody from the Ubuntu community assumes this job (i.e. a package maintainer). So, if there is any volunteer... BTW: have you tried installing the .deb packages that are already available on [1]?

Regarding the packages you found in lihuen repository I should say that I'm proud with this people, but I have no control over this distribution. So, perhaps you may want to suggest them to release an updated version...

[1] [http://viacam.org](http://viacam.org) 

No hay de que

---

### Post by Alex 999 on 2010-02-24
Thanks for the info. Which distros support Eviacam aside from Debian? I didn't know about the others so I am curious to know.

Version 1.0.1 runs nicely on an updated Ubuntu 9.10. I'm enjoying it but find it near impossible to write in. I could never have typed this with it and Kvkbd. However it works just fine otherwise. I am using a infrared device in Windows called SmartNav 4 which cost me over $500 USD. I'm thrilled to see your program work but now your saying that you have no control over this version. 

Yes me and Sean have tried the deb files and have endless dependency problems. For instance libavformat0d keeps showing up on the error messages even after I install it and all the other lib files. Is there a big difference between version 1.0.1 and 1.2?

Please let us know of any developments and, again muchas gracias






Venceremos!

---

### Post by cmauri on 2010-03-06
Hi all,

eViacam ([http://viacam.org](http://viacam.org)) version 1.2.1 is out including Ubuntu karmic .deb pre-compiled binaries for 32 and 64 bit platforms. 

After downloading install using GDebi (i.e. making double click).

Have fun.

---

### Post by Sean Moran on 2010-03-10
> **cmauri said:**
> Hi all,

eViacam ([http://viacam.org](http://viacam.org)) version 1.2.1 is out including Ubuntu karmic .deb pre-compiled binaries for 32 and 64 bit platforms. 

After downloading install using GDebi (i.e. making double click).

Have fun.

Dear Cesar,

Alex skyped me the good news last night, and although I am only just planning on downloading the new version of eViacam 1.2.1 this afternoon to try out and add to the Lynx ViaBuntu distribution next week when the Beta is released, I wish to thank you for perfecting an Ubuntu version in simple .deb format that people like me can work out how to install without tears.  Alex tells me that the minor bugs in the 1.0.1 version he found on the lihuen repository have been overcome and this version of eViacam works like a treat.

It must have been a fair bit of work on your part, to get this version ported to Ubuntu so soon, so thank you for making such a good effort, and I hope to report back later this afternoon after I've had a chance to download the newie and see if it's as grand as Alex tells me.

Yours Sincerely,

Sean Moran.

:popcorn:

It certainly looks a lot more polished, with the improved layout on the configuration dialogs, the graphic icons in the click window, and increasingly smooth cursor movement.  I can understand why Alex was pleased with the new version last night and I am rather stoked myself after only ten minutes of trying it out.  All I can say now is that installing eViacam onto Ubuntu 9.10 has now become VERY easy.

Sincere thanks to Cesar and contributors:

Julian Aloofi, AluminiuM, Christian Bieder, Miguel Bouzada, Antonio Capone, Carles Garrigues, Karl L. Gechlik, Sebastien Lecointre, Giuseppe Masciopinto, Alessandro de Olivera Faria, Anil Ozbek, Samuel Thibault, Aldo Maria Vizcaino, Theodore Watson, and many others.

---


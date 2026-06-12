---
title: "[SOLVED] ./configure... makefile failed... help"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by goldencj on 2007-12-27
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ ./configure
# Basic Settings
Compile type     release
Compiler cache   no
DistCC           no
Install prefix   /usr/local
CPU              x86 (model name        : mobile AMD Athlon(tm) XP-M 1600+)
Big Endian       no
MMX enabled      yes

# Input Support
Joystick menu    yes
lirc support     no
Apple Remote     no
Video4Linux sup. yes
ivtv support     yes
FireWire support no
DVB support      no [/usr/include]
DBox2 support    yes
HDHomeRun sup.   yes
CRC Ip Rec sup.  yes
FreeBox support  yes

# Sound Output Support
OSS support      yes
ALSA support     no
aRts support     no
JACK support     no
DTS passthrough  no

# Video Output Support
x11 support      yes
xrandr support   yes
xv support       yes
XvMC support     no
XvMC VLD support no
XvMC pro support no
XvMC OpenGL sup. no
Mac accel.       no
OpenGL vsync     no
DirectFB         no

# Misc Features
Frontend         yes
Backend          yes

# Bindings
bindings_perl    no
Creating libs/libmyth/mythconfig.h and libs/libmyth/mythconfig.mak

Failure to open file: /home/tlc/Desktop/mythtv-0.20.2/Makefile
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ make
make: Makefile: Too many levels of symbolic links
make: stat: Makefile: Too many levels of symbolic links
make: *** No rule to make target `Makefile'.  Stop.
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ sudo make install
Password:
make: Makefile: Too many levels of symbolic links
make: stat: Makefile: Too many levels of symbolic links
make: *** No rule to make target `Makefile'.  Stop.
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ ./configure
# Basic Settings
Compile type     release
Compiler cache   no
DistCC           no
Install prefix   /usr/local
CPU              x86 (model name        : mobile AMD Athlon(tm) XP-M 1600+)
Big Endian       no
MMX enabled      yes

# Input Support
Joystick menu    yes
lirc support     no
Apple Remote     no
Video4Linux sup. yes
ivtv support     yes
FireWire support no
DVB support      no [/usr/include]
DBox2 support    yes
HDHomeRun sup.   yes
CRC Ip Rec sup.  yes
FreeBox support  yes

# Sound Output Support
OSS support      yes
ALSA support     no
aRts support     no
JACK support     no
DTS passthrough  no

# Video Output Support
x11 support      yes
xrandr support   yes
xv support       yes
XvMC support     no
XvMC VLD support no
XvMC pro support no
XvMC OpenGL sup. no
Mac accel.       no
OpenGL vsync     no
DirectFB         no

# Misc Features
Frontend         yes
Backend          yes

# Bindings
bindings_perl    no
Creating libs/libmyth/mythconfig.h and libs/libmyth/mythconfig.mak

libs/libmyth/mythconfig.h is unchanged
Failure to open file: /home/tlc/Desktop/mythtv-0.20.2/Makefile
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$

---

### Post by SOULRiDER on 2007-12-27
Check this out
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by Bloch on 2007-12-27
Hi goldencj;

You are trying to compile a program from the source code. That's not for beginners. Ubuntu does not have the required compilers & libraries built in.

Linux users don'\t have to compile software these days. Sure, it might be interesting and fun to test-drive the latest versions before anyone else, and you get my respect if you want to go down that road.

Tell us what program you need, and why you want to compile it rather than install from Synaptic / Add/Remove feature.

---

### Post by SOULRiDER on 2007-12-27
I'm guessing the program is MythTV sicne that seems to be the directory he is in. The link I posted shows how to install it on ubuntu. Check it out.

---

### Post by William S on 2007-12-27
If the program is available in Synaptic download it from there and the system takes care of updates. :)

---


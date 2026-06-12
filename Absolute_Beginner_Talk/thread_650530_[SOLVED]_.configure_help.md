---
title: "[SOLVED] ./configure help"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by goldencj on 2007-12-26
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
xrandr support   no
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
./configure: line 3510: qmake: command not found
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ dir
AUTHORS      config.h    COPYING   i18n         Makefile      tests
bindings     config.log  database  keys.txt     mythtv.pro    themes
config       config.mak  docs      libavcodec   programs      UPGRADING
config.err   configure   FAQ       libavformat  README        version.pro
configfiles  contrib     filters   libs         settings.pro  vhook
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ ./config
bash: ./config: is a directory
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ cd config
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2/config$ dir
Makefile
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2/config$ ./configure
bash: ./configure: No such file or directory
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2/config$ cd
tlc@tlc-desktop:~$ sudo ./configure mythtv-0.20.2
sudo: ./configure: command not found
tlc@tlc-desktop:~$ cd Desktop
tlc@tlc-desktop:~/Desktop$ cd mythtv-2.20.2
bash: cd: mythtv-2.20.2: No such file or directory
tlc@tlc-desktop:~/Desktop$ cd mtthtv-0.20.2
bash: cd: mtthtv-0.20.2: No such file or directory
tlc@tlc-desktop:~/Desktop$ cd mythtv-0.20.2
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$ dir
AUTHORS      config.h    COPYING   i18n         Makefile      tests
bindings     config.log  database  keys.txt     mythtv.pro    themes
config       config.mak  docs      libavcodec   programs      UPGRADING
config.err   configure   FAQ       libavformat  README        version.pro
configfiles  contrib     filters   libs         settings.pro  vhook
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
xrandr support   no
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
./configure: line 3510: qmake: command not found
tlc@tlc-desktop:~/Desktop/mythtv-0.20.2$

---

### Post by Cypher on 2007-12-26
You're going to need the either QT3 or QT4 tools depending on what MythTV wants..So check on the website to see what they say..

For QT3 do
```

sudo apt-get install qt3-dev-tools

```

For QT4 do
```

sudo apt-get install libqt4-dev

```

---

### Post by goldencj on 2007-12-26
Thank you verry muchly!

---


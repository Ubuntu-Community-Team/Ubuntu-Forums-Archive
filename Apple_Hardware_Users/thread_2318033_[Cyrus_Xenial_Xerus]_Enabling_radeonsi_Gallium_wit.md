---
title: "[Cyrus_Xenial Xerus] Enabling radeonsi Gallium with Mesa ?"
date: 2016-03-22
forum: Apple Hardware Users
---

### Post by Sinan_Grkan on 2016-03-22
Hello

I have compiled Mesa-Git with radeionsi gallium driver on my Cyrus (A-Eon X5000 e5500 based motherboard)
I have Radeon R7 265 graphic card.

I am running Xenial Xerus (development branch)

I used following configuration 

sudo sh ./autogen.sh --prefix /usr/local/mesa-git --with-gallium-drivers="radeonsi" --enable-texture-float --enable-gallium-llvm --with-egl-platforms=drm --enable-dri --enable-dri3 --enable-xa --enable-gbm --enable-omx --enable-shared-glapi --enable-glx-tls

make install completed without problems.

However when I run glxgears, system uses the software driver.

What should I do now to enable radeonsi ?

My Xorg.conf is this:

Section "ServerLayout"
Identifier "Desktop"
Screen 0 "Screen0" 0 0

InputDevice "Mouse0"   "CorePointer"
#InputDevice "Keybard0"  "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
EndSection
Section "Module"
Load "glx"
Load "dri"
Load "dri3"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Device"
Option "glx" "1"
Option "dri" "1"
Option "dri3" "1"
Identifier "Card0"
Driver "radeon"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Subsection "Display"
Viewport 0 0
Depth 1
EndSubSection

Subsection "Display"
Viewport 0 0
Depth 4
EndSubSection

Subsection "Display"
Viewport 0 0
Depth 8
EndSubSection

Subsection "Display"
Viewport 0 0
Depth 16
EndSubSection


Subsection "Display"
Viewport 0 0
Depth 24
EndSubSection

EndSection

---


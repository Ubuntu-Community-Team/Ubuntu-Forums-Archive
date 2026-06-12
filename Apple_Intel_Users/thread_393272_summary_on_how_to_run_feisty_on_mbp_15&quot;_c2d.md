---
title: "summary on how to run feisty on mbp 15&quot; c2d"
date: 2007-03-25
forum: Apple Intel Users
---

### Post by alvinwu on 2007-03-25
Hi everybody, I like to share my works on how to run Ubuntu (7.04) on my mbp 15", although it is not perfect, I feel I can working happily with it. Therefore I want to share with you and hope that can give some points to those Ubuntu developers. 

Please correct me if I'm sharing something incorrect..

1) install
>> refer to other url for details
if facing problem at the very last stage, remember:
reboot and use refit to sync the gpt/mbr hybrid partitioin
reboot using Ubuntu livecd  (I use the desktop-amd64.iso)
mount your target partition, most likely is /dev/sda3
cd to that mount point
mount -t proc proc proc
mount -t sysfs sysfs sys
mount -o bind /dev dev
chroot . /bin/bash
grub-install "(hd0,2)"
parted /dev/sda print
check that the /dev/sda3 boot flag is on

if not, you may need to set the boot flag on and reboot and resync using refit...then repeat the steps above.

After successfully bootup, remove mouseemu (this creates problem with pommed).

2) Using touch pad, enable right-click

do not install GUI synaptics touchpad program, this is real slow ..I use the following xorg.conf:


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"

        Option "LeftEdge" "10"
        Option "RightEdge" "1210"
        Option "TopEdge" "10"
        Option "BottomEdge" "375"
        Option "FingerLow" "0"
        Option "FingerHigh" "3"
        Option "MaxTapTime" "100"
        Option "SingleTapTimeout" "100"
        Option "MaxTapMove" "20"
        Option "MaxDoubleTapTime" "150"
        Option "VertScrollDelta" "8"
        Option "HorizScrollDelta" "8"
        Option "VertEdgeScroll" "false"
        Option "HorizEdgeScroll" "false"
        Option "VertTwoFingerScroll" "true"
        Option "HorizTwoFingerScroll" "true"
        Option "FastTaps" "false"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "MinSpeed" "0.7"
        Option "MaxSpeed" "8.0"
        Option "AccelFactor" "0.45"
                Option "SHMConfig"      "on"
        Option          "SHMConfig"             "true"  
EndSection

This enables two finger tap = "right click"

3) keyboard

When pommed has been installed and start up correctly.

I use a simple ~/.Xmodmap file to have

right-end-side little enter = "delete"
right-hand-side apple command button = "right-alt"
F1-F2, F3-F5,F8-F10 maps to backlight, sound control, keyboard backlight
fn+F!...F12 >> normal function key
fn+ARROWS = home, end, page up, down ..etc

~/.Xmodmap file contains:
 
keycode 115 = ISO_Level3_Shift
keycode 108 = Delete
keycode 98 = Up Prior
keycode 104 = Down Next
keycode 100 = Left Home
keycode 102 = Right End
keycode 22 = BackSpace Insert
keycode 116 = Alt_R
add Mod1 = Alt_L
add Mod2 = Mode_switch


4) fglrx for 2D/3D support

use synaptics package management, install restricted modules vs the kernel version, and the xorg driver 

check your xorg.conf:

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSections

reboot, use fglrxinfo to check and glxgears to test....

5) sound

check "line in as output" of your volume control
also check for front, lfe, surround, .. etc, and listen to the beautiful sound from the internal speakers..

6) fglrx, openoffice, scim

problem when the above combination....

temp fix:

create ~/.xinput.d/all_ALL
edit and fill in the text "export LC_CTYPE=zh_HK.UTF-8"
open preference/sessions and create "scim -d" as startup program
reboot and I can start openoffice now...

7) cannot boot sometimes after kernel upgrades

refer to step (1) to fix it
OR
modify /boot/grub/menu.lst and change default to whatever the previous kernel works

fglrx may not work at this stage, no 3D .. noway, way for next kernel fix , then reinstall the restricted package...AND modify your menu.lst setting !

---------------------------

Although there are other issues, such as iSight, madwifi, some application crashes, I can use it happily now! I can use wammu to work with my Nokia 6280 mobile phone :) 

BTW, for Chinese fonts, if you have the legal license......

copy MS mingliu... simsun TT fonts into /usr/share/fonts/MS/ ....
then run (as root) fc-cache -vf

you now have a relatively good looking Chinese font....

BTW, you can change your fonts setting to fit LCD display.

8) change your system boot wait time >>

refit > change (the OSX partition) /efi/refit/refit.conf "timeout" value
grub > change /boot/grub/menu.lst "timeout" value

I recommend using gkrellm and cairo-clock and set it up to show pretty system status.

Hope everyone can have a usable Ubuntu Linux on Macbook Pro, show it to your friends...
Welcome everyone to share their experience with me..

---

### Post by ronocdh on 2007-04-02
Thanks for the guide, it looks quite slick. Unfortunately, my C2D MBP 15" is throwing a fit everytime I try to install Feisty: I can't get Xserver to start! I have checked all the burns many times, tried both i386 and 64-bit versions... nothing.

I've tried using the cevesa "safe graphics" mode. Nothing. Did you encounter anything like this at all? I'm currently writing on a rock stable 6.10 i386 with fglrx (although no 3D acceleration yet).

---

### Post by davidsiegel on 2007-04-02
Thank you for your guide. Do you think you can clean it up a bit? It looks like it has a lot of valuable information for MacBook Pro C2D prospective Feisty users like me, but it looks like you wrote it in three minutes. If you could be a bit more thorough, it would be very appreciated.

---

### Post by Chrisj303 on 2007-04-03
The first bit can be solved a lot easier though - once youve installed the refit.deb, and are about to commence installing ubuntu, open up a terminal:

sudo gptsync /dev/sda && sudo sfdisk -c /dev/sda 3 83 -DO NOT PUSH ENTER!!

Then start the installer - when it says 'copying files' go back to your terminal NOW PUSH ENTER!
This will re-sync the tables and allow ubuntu to be installed without grub crashing.


chrisj303

---


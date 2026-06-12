---
title: "Help To install Nvidia GeForce 7800 GT"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Ashtarot on 2006-11-30
ok, im new in lnux, id like to learn how to install my video card properlly, I found this file in the Nvidia linux drivers page:

NVIDIA-Linux-x86-1.0-9629-pkg1.run

first of all is this file right for my video card?

second, i tryed to follow the instruccitions on the nvidia page but ...... first i got the...... you still have a x server running, so i looked it up and i found how to kill the Xserver...... but the command i got also got me out of the graphic interface.. is this normal???

whille i was out of the graphic interface i tried again to install the driver...... but i got another error..... that there was no precompiled driver for my kernel version or smth like that... i couldnt take notes since i didnt have graphic interface..... so..... how do i know wich kernel version do i have ??? and how do i fix the problem with the kernel version ?

---

### Post by Perfect Storm on 2006-11-30
If you have the file on the Desktop:
```

cd && cd Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo /etc/init.d/gdm start
```

You might print it out, because it needs that you are not in X.

You know that's an easy way to get the 3D driver by using synaptic package manager?

---

### Post by Ashtarot on 2006-11-30
Thanks.... and no.. i didnt know... either way thanks for the help

---

### Post by Perfect Storm on 2006-11-30
Synaptic package manager: System tab ---> Adminstration ---> Synaptic package manager

Here you can find and install applications and stuff with ease, but any case here's how you do it through the terminal;
```
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

restart X (ctrl + alt + backspace)

If it doesn't work report back.

---

### Post by Ashtarot on 2006-12-01
I tried using synaptic....... then i re started X.. but now i get an error that the X server isnt right and now i can only use the terminal........ so.......

ill try to fix it using the terminal and report back on how it turns out

---

### Post by rev_b on 2006-12-01
Much easier:
Install automatix- it´s a .deb package, it´ll self install
 
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-1.11-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-1.11-6.10edgy_i386.deb)

Then run it and select it to install Nvidia drivers. It'll download and do everything in the background, even configure your xorg.conf file. It'll prompt you at the end for a restart, you don't really to, just ctrl+alt+backspace to restart X and login again.

While at it, install some codecs, fonts, plugins, and other apps you may need.

It works wonders with my 7900GT, so it should work for you.

---

### Post by Ashtarot on 2006-12-01
There is a little problem now.......... the x server dosnt work anymore.... when i try to start it ( /etc/init.d/gdm start)it just says..... Fail

well i heard there is a 64 bit edition for ubuntu.... but i already hae the i386 installed...... maybe ill use this chance to see how it works for me.... and maybe ill try automatix and see how it works.

Thanks, i still want to make it work(i dont like formating my HD specially if i dont have to)  so if anyone could help me ill really apreciate it, ill keep an eye on this tread....... unfortunately..... i have to reboot my pc every time to try a  new solution so please be patient..

---

### Post by Perfect Storm on 2006-12-01
Okay, do this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
```

reboot

If it doesn't work:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf
```

Go to the **Section "Screen"** and change **"nvidia"** back to **"nv"**

save and exit (ctrl + o) (ctrl + x)

---

### Post by Ashtarot on 2006-12-01
The strangest thing happend, lasnight i tryed the solutions abobe(all except the last one to restore the backup file), but it didnt seemed to work, so i rebooted and started in windows so i could enter this forum, im mexican, since no other replies wer posted unitil 1 AM i went to sleep. Today y saw the last post and y rebooted to try to what it said..... the strange thing was....... Ubuntu started in graphic mode without any ploblem..... so it seems that something that i tried lastnight worked....

it semms like the Driver didnt helped a lot since in windows my resolution gango up till 1200 *  1058  and in ubuntu it can only go till 1024 * 768 
and before i aplied the driver the refresh rate was 80 Hz, and now it goes only till 50 Hz.   is This Normal ???

Well Thanks For Your help So far.

---

### Post by Perfect Storm on 2006-12-01
Please post your xorg.conf file.

---

### Post by Ashtarot on 2006-12-02
Here's my xorg.conf File, sorry it took me so long, i couldnt be homm all day

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Perfect Storm on 2006-12-02
Are you sure you have Nvidia card?

> Section "Device"
Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Driver "nvidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Monitor "Generic Monitor"

---

### Post by Ashtarot on 2006-12-02
> **Artificial Intelligence said:**
> Are you sure you have Nvidia card?

Im quite sure........ actually before i log into my ubuntu acount i get an Nvidia Screen, and im really sure my card is nvidia geforce 7800 GT, it says so on the box, the card, on the manual...... u know what i mean, and since i share my pc with my brothers wh only use it to play i have a windows also installed, and it works "perfect" (as perfect as posible in windows)

---

### Post by testbenchdude on 2006-12-03
Automatix2 is my new best friend. Installed drivers for my 7900GTs (sli) flawlessly. Woot!

---

### Post by Perfect Storm on 2006-12-03
> **Ashtarot said:**
> Im quite sure........ actually before i log into my ubuntu acount i get an Nvidia Screen, and im really sure my card is nvidia geforce 7800 GT, it says so on the box, the card, on the manual...... u know what i mean, and since i share my pc with my brothers wh only use it to play i have a windows also installed, and it works "perfect" (as perfect as posible in windows)

Well, then something is completly wrong. As in your xorg.conf it's sen as an ATI card.
Are you sure you have put the correct information with sudo dpkg-reconfigure -phigh xserver-xorg?

---

### Post by Ashtarot on 2006-12-03
> **Artificial Intelligence said:**
> Well, then something is completly wrong. As in your xorg.conf it's sen as an ATI card.
Are you sure you have put the correct information with sudo dpkg-reconfigure -phigh xserver-xorg?

I dont think i got to that part, when i had no graphic interface i was about to try that one but i didnt get to doit since the graphic interface magicly(i.e. I have no idea how it happend bit it did) worked. i tough those lines where to restore the previous configuration so since the new one seemed to work i didnt saw the need to do it. Was I supose to????

---

### Post by Ashtarot on 2006-12-03
> **Artificial Intelligence said:**
> Well, then something is completly wrong. As in your xorg.conf it's sen as an ATI card.
Are you sure you have put the correct information with sudo dpkg-reconfigure -phigh xserver-xorg?

Im sorry i havent been home a lot lately, that command...........  i didnt get to excecute it, since i tough it was just to restore the previous seetings, since i had no graphic interface at the momment u segested it so since something made the gnome work... aparently the way it shuld.. i didnt bother in trying it

---

### Post by Ashtarot on 2006-12-04
ok, i tried to re install my driver, it seemed to work...... but my xorg.conf file has this:

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"NoLogo"
EndSection

the no logo part  was added by me but what bothers me is the "default card" part.......... isnt it supose to say...... Nvidia GeForce 7800 GT  or something like that???

The same happends in the screen part.

What  should i do????

---

### Post by Perfect Storm on 2006-12-04
If it runs 3D without any problems, there's no reason to change it.

---

### Post by Ashtarot on 2006-12-04
ok thanks for all the help and time

---

### Post by Perfect Storm on 2006-12-04
You're welcome. If any problem shows up with it later you know where to post it ;)

---


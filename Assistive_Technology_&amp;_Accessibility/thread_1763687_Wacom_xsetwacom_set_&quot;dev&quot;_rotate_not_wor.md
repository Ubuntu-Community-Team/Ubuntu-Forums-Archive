---
title: "Wacom: xsetwacom set &quot;dev&quot; rotate not working"
date: 2011-05-20
forum: Assistive Technology &amp; Accessibility
---

### Post by Sidion on 2011-05-20
Hello, I am running ubuntu 10.10 on a HP compaq tc4400 tablet laptop.

The tablet pen is functioning as expected but the xsetwacom set rotate command is not.

eg:
sidion@tablet:~$ xsetwacom get "Serial Wacom Tablet stylus" rotate
1
sidion@tablet:~$ xsetwacom set "Serial Wacom Tablet stylus" rotate 0
sidion@tablet:~$ xsetwacom get "Serial Wacom Tablet stylus" rotate
1

I have tried both numerical values eg: 0, 1, 2, 3 and word values: NONE, CW, CCW

It also seems that other assignments via xsetwacom are not working:

sidion@tablet:~$ xsetwacom get "Serial Wacom Tablet stylus" Button1
1
sidion@tablet:~$ xsetwacom set "Serial Wacom Tablet stylus" Button1 2
sidion@tablet:~$ xsetwacom get "Serial Wacom Tablet stylus" Button1
1


Also the gui program wacomcpl does not list any devices.
Any assistance in this problem would be greatly appreciated.

for reference:
sidion@tablet:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys     

sidion@tablet:~$ xsetwacom list dev
SynPS/2 Synaptics TouchPad touch     
Serial Wacom Tablet eraser eraser    
Serial Wacom Tablet stylus stylus

sidion@tablet:~$ cat /usr/share/X11/xorg.conf.d/50-wacom.conf 
Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

---

### Post by firestormfury on 2012-06-19
This also describes my problem, dose someone know what's going on? It used to work some years a go back in Ubuntu 8.10.

A solution for me would be to set ccw as default because I only really want to use the pen when the screen is rotated.

Cheers!

---

### Post by Favux on 2012-06-19
Hi firestormfury,

Welcome to Ubuntu forums!


Ususally this indicates you don't have screen rotation enabled for your video chipset:
```
lspci | grep VGA
```
It most often happens with the Nvdia proprietary driver.  Check your xorg.conf and make sure the line:
```
	Option "RandRRotation" "on"
```
is present.  An example section:
```
Section "Device"
	Identifier "Default Device"
	Option "RandRRotation" "on"
	Option	"NoLogo"	"True"
	#	Identifier "n"
	#	Driver "nouveau"
EndSection
```
You can use:
```
gksudo gedit /etc/X11/xorg.conf
```
Always remember to make a backup of your current working xorg.conf, if you have one, so you can restore it from the command line if you break X.

See appendix 1 on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").

---

### Post by wildmanne39 on 2012-07-24
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---


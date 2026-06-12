---
title: "Failed to start the X server"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Gwalk on 2005-11-20
Hi,
I just installed Ubuntu 5.10 on my computer and get the error "failed to start the X server" I get the same thing when booting from the hard drive or trying to boot from the live cd.

I am a real Linux newbie here, never been able to get a Distro running. tried Red Hat, Fedora Core, FC-2 and now Ubuntu and there always seems to be an issue.

Some Specs:
 Mobo: Abit AA8XE
 Video: ATI Radeon X700 Pro (PCI-express)
 Proc: Intel P4 3.06
 Ram: Pny DDR2  1024 MB

In part screen shows:

Module Loader present
OS Kernel: Linux version 2.6.12.9-386 (GCC version 3.4.5 20050809 (pre release) (Unbuntu 3,4,4-6 ubuntu8)) #1 Mon Oct 18 (**) from config file

Can anyone help me get this OS going ?

Thank You

---

### Post by thomas.mcmahon on 2005-11-20
Hi Gwalk,

I'd love to help you get it going :) Not getting X running is without a doubt *the* most annoying problem when installing linux, but it is solveable.

First of all could you please type this from the command prompt that you get when X won't load.

sudo dpkg-reconfigure xserver-xorg

This will resetup your xserver, try going through this and answering as many of the questions as you can, if you can't answer the question just accept the default, then see if it works after that. If not we'll have to try something else. :)

---

### Post by Gwalk on 2005-11-21
Hi Thomas,
I entered the line as you suggested at the command prompt:
Attempt auto detect: yes
Desired X server driver: ATI
Enter Identifier: Radeon X700 Pro (Rv410) (this was default)
Users of multi head setup..see file /etc/x11/xorg.conf
  In Windows Device Manager I show A Radeon X700 Pro, PCI bus 1,device 0. function 0 AND a Radeon X700 Pro Secondary, PCI bus 1, device 0, function 1
 This motherboard doesn't have a AGP,slot, PCI-E 16x for video, two PCI-e 1x and two regular PCI slots.

Enter the video cards bus Id: PCI:1:0: (default value)
enter amount of RAM: left blank
Use kernel framebuffer: yes

I selected 1024x768@75 and 24 bit color depth

I entered  startx
got the following error

[EE] No devices detected
check log file at  /var/log/Xorg.0.log
XIO: Fatal IO error 104 (connection reset by peer) on X server

What can I try next. Why does my video card show up as two display adoptors in Windows ?

---

### Post by rjwood on 2005-11-21
Hi Gwalk,  Can you please post your xorg.conf file---from command line

```
sudo nano /etc/X11/xorg.conf
``` 
copy and paste,also look at the /var/log/Xorg.0.log  highlight anythig with [EE] and post that as well

---

### Post by Gwalk on 2005-11-22
Hi,
I tried to look at /etc/X11/xorg.conf  All I got was a empty screen. I looked at /var/log/Xorg.0.log and the file was BIG, thing is I am very unfamiliar with Linux and it was all greek to me. I would have liked to copy and paste the file but I don't know how to do that. Can you give me some step by step guidence on that ?

---

### Post by Brunellus on 2005-11-22
gwalk:  remember that the bash shell is case sensitive.  look again:  /etc/X11/xorg.conf has a capital X in X11

---

### Post by Gwalk on 2005-11-23
I was able to see /etc/X11/xorg.conf  and  /var/log/Xorg.o.log
Can someone tell me how copy these files to floppy disk so that I may post them here. I have always used some version of Windows in the past and working from a command line in Linux is very difficult for me.

some info from the files:

Section "Device"
Identifier: ATI Tech Radeon X700 Pro (RV410)
Driver:  ATI
Bus ID:  PCI:1:0:0

Section "Monitor"
ID: Generic Monitor
Option: DPMS
H Sync: 30-70
V Sync: 50-160

Is the bus ID correct? In Windows this video card shows a Primary and a Secondary

During bootup the display shows a colorful screen "Unbuntu" with the loading moduals in red until a certain point then switches to a black screen with white block letters.

---

### Post by thomas.mcmahon on 2005-11-23
Try changing your driver from ATI to "vesa" this will probably get your x server pumping, but you will want to change the driver later on as vesa will give you a sluggish x server.

---

### Post by towsonu2003 on 2005-11-23
[QUOTE=Gwalk]
Section "Device"
Identifier: ATI Tech Radeon X700 Pro (RV410)
Driver:  ATI
Bus ID:  PCI:1:0:0

Is the bus ID correct?[/QUOTE]

It usually is correct. To check, type lspci than compare the output for the device with that in your xorg.conf. Here is my comparison (ati radeon 9100 something):

In lspci:
0000:**01:05.0** VGA compatible controller: ATI Technologies Inc: Unknown device 5835

In xorg.conf:
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9100 IGP"
        Driver          "ati"
        BusID           "PCI:**1:5:0**"
        VideoRam        131072
        Option          "UseFBDev"              "true"

Sorry can't help with the rest, I'm too newbie for that :) good luck though (I know the feeling...)

---

### Post by xelink on 2005-11-24
[QUOTE=thomas.mcmahon]Hi Gwalk,

I'd love to help you get it going :) Not getting X running is without a doubt *the* most annoying problem when installing linux, but it is solveable.

First of all could you please type this from the command prompt that you get when X won't load.

sudo dpkg-reconfigure xserver-xorg

This will resetup your xserver, try going through this and answering as many of the questions as you can, if you can't answer the question just accept the default, then see if it works after that. If not we'll have to try something else. :)[/QUOTE]

dude, I love you, have my babies(not really)

you just saved me from having to reinstall linux, I was having a pain trying to install drivers(I guess they are installed now it autodetected my card) I ended up F'ing up Xserver... thanks God for this...

---

### Post by Gwalk on 2005-11-24
Thanks All,
Some progress here:

I entered:  sudo dpkg-reconfigure xserver-xorg
  selected the vesa driver instead of the ATI driver

entered:  startx

and it WORKED !

I don't have any sound but at least I have an internet connection and a GUI

Thank you

---

### Post by thomas.mcmahon on 2005-11-24
[QUOTE=xelink]dude, I love you, have my babies(not really)

you just saved me from having to reinstall linux, I was having a pain trying to install drivers(I guess they are installed now it autodetected my card) I ended up F'ing up Xserver... thanks God for this...[/QUOTE]

Haha, no worries it's a pleasure :)

---

### Post by thomas.mcmahon on 2005-11-24
[QUOTE=Gwalk]Thanks All,
Some progress here:

I entered:  sudo dpkg-reconfigure xserver-xorg
  selected the vesa driver instead of the ATI driver

entered:  startx

and it WORKED !

I don't have any sound but at least I have an internet connection and a GUI

Thank you[/QUOTE]

Glad to see man, now that your x-server is working you can probably work out why your video wasn't working. Maybe have a look on the ATI site and get their proprietary drivers so that you can get 3d etc. because you'll notice that the VESA drivers make your Xorg a little bit slow. Not urgent of course, good to see we fixed the problem :)

---

### Post by Fittersman on 2005-11-24
I am having the exact same problem as gwak its driving me nuts. I got a lot of info posted on

Ubuntu Forums  --> Ubuntu Breezy Badger 5.10  -->Ubuntu 5.10 Support (GNOME)  --> X server problem 

so if you could use both of our info together it might help out alot with solving hte problem

---

### Post by Fittersman on 2005-11-24
nothing you guys told him worked for me i dont know what to do now. well if you could tell me where to type in that dkpg thing it might work because i couldnt find where to type it in.

---

### Post by xelink on 2005-11-24
[QUOTE=Fittersman]nothing you guys told him worked for me i dont know what to do now. well if you could tell me where to type in that dkpg thing it might work because i couldnt find where to type it in.[/QUOTE]

you type it into command line, either in terminal, or if your system won't fully start up the basic command line which you are forced to be in.

---

### Post by Fittersman on 2005-11-24
tried that and it gave me an error something about users but im not sure if you need the exact error message i can get it for you.

---


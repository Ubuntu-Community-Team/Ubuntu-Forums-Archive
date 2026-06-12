---
title: "I can't seem to get this to work =("
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Kos-Mos on 2006-10-17
I have absolutely tried everything. In the process I must of destroyed 10+ discs and am starting to get frusterated. I can't seem to get ubuntu to boot up after installation.

Ok, well here are all the things I have tried so far:

1) Using the alternate-i386 version is the only version that will boot up. So its the only version I have been able to use.

2) When trying the desktop-i386 version, I kept getting "Selected boot device is unavailable", I realized that it was how I was burning the dvd... So I went and tried to write the dvd a suggested way and still didnt work. At this point I started getting frusterated at losing discs so I switched to a dvd+rw and wrote the .iso file in nero as a dvd boot disc

3) Now that I have dvd+rw with the iso on it as a boot disc, it actually booted up, but it started up Caldera DR-DOS for some reason and I couldnt do anything at all.

The problem with the alternate version when starting up, is that when the part to log on is about to come, the screen gets all scrambled with bright colors and my computer freezes.

My partition table is currently set up as:

1) Windows XP
2) Swap area
3) Ubuntu
4) Logical Partition

I dont think the partition table has anything to do with it because I remember trying to just format completely to Ubuntu and not be dual booted and got the same problem.

I would really like to get this thing working, any help would be greatly appreciated ^_^.

---

### Post by bulldog on 2006-10-17
It's a good thing to let Ubuntu makes his own partitions.

Just leave the space you wanna use for Ubuntu unallocated.

It shouldn't matter but it does some how.

When the partitioner comes up you can decide to partition manually or let ubuntu decide,but making partitions on forehand is not a good thing.

---

### Post by dannyboy79 on 2006-10-17
just a tip for you, you would get more people to help you if you had a better subject line for your post. Now when you say, "alternate version when starting up, is that when the part to log on is about to come, the screen gets all scrambled with bright colors and my computer freezes" doesn't make sense because I used the alternate install cd and there is no part where you log on? It sounds like you may be having some kind of vga problem, you should gogle "vga boot options for ubuntu" and see what you can find.

---

### Post by monktbd on 2006-10-17
> **Kos-Mos said:**
> 3) Now that I have dvd+rw with the iso on it as a boot disc, it actually booted up, but it started up Caldera DR-DOS for some reason and I couldnt do anything at all.


you need to burn the disc as an iso-image not as a bootable disc.
i dont know if it works with a dvd properly, a cd should do.

> 
The problem with the alternate version when starting up, is that when the part to log on is about to come, the screen gets all scrambled with bright colors and my computer freezes.


sounds like a problem with the x-server, can you select the recovery mode from the grub boot menu?

---

### Post by Kos-Mos on 2006-10-17
Ok, sorry about that. Well, when ubuntu is starting up after installing and its giving all those ok messages to things that its starting up, right after that is when the screen gets scrambled and the computer freezes, I am just presuming you log on after that due to a video I seen online. There is NO log on point before that =P.

Also, I am quite sure I tried letting ubuntu make its own partitions before. I will try again though >_<.

---

### Post by Kos-Mos on 2006-10-17
I can select recovery mode, but then that screws up to. Something about "optimum resolution 1280x1024 60hz cannot display". I tried burning it as an iso image and get the message "Selected boot device is not available".

---

### Post by bulldog on 2006-10-17
> **Kos-Mos said:**
> Ok, sorry about that. Well, when ubuntu is starting up after installing and its giving all those ok messages to things that its starting up, right after that is when the screen gets scrambled and the computer freezes, I am just presuming you log on after that due to a video I seen online. There is NO log on point before that =P.

Also, I am quite sure I tried letting ubuntu make its own partitions before. I will try again though >_<.

Well you have already installed Ubuntu :D thought you're on the cd before install.

Is the Xserver crashing with a blue screen?
Drropping you on a commandline?

If so login there and type```
sudo dpkg-reconfigure -phigh  xserver-xorg
```
and choose a lower resolution.

After you get into Ubuntu install your graphic's drivers and choose the desired resolution.

---

### Post by Kos-Mos on 2006-10-17
Ok, I will show you a video of roughly where it crashes.

[http://www.youtube.com/watch?v=x0A1xIFdIhQ](http://www.youtube.com/watch?v=x0A1xIFdIhQ)

Ok, where his screen gets the white dot in the center, is where mine gets all colorful and scrambled and my computer freezes.

When I press the power button on the tower, it drops from that screen to something like a commandline that I can't use. It says

Hostname login:

then my computer crashes after a few seconds.

---

### Post by monktbd on 2006-10-17
so i guess hitting ctrl-alt-f1 to frop you to a terminal doesnt help there either?
with "there" i mean when the color flashing started?
if you get to the terminal do what bulldog suggested with reconfiguring xorg

if the recovery doesnt work then your vga settings arent working for the recovery mode (and also then for the terminal with the normal boot).

---

### Post by bulldog on 2006-10-17
Well can you actually login,and what you mean with crash,is it not responding to you or is it going to explode or what.

---

### Post by Kos-Mos on 2006-10-17
By crash I mean that my computer automatically turns off.

I do have good news, I can get into recovery mode, its when I use the command to exit that I get that "Optimum Resolution 1280x1024 60hz" error. Sorry, I should of double checked... I have been up all night trying to get this to work.

I will try that to monktbd

---

### Post by monktbd on 2006-10-17
if you can get the recovery mode working just try the reconfiguration of the xserver there.

---

### Post by Kos-Mos on 2006-10-17
Ok, I got it to work through the recovery mode. Also, when doing your ctrl+alt+F1 it did drop me down to a command line. The same one when I click the power button but this time I could login and everything. 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

worked in both, but I have no idea what to do when it brings the video mode stuff up.

---

### Post by bulldog on 2006-10-17
Sorry posting twice.

---

### Post by bulldog on 2006-10-17
Select the desired resolution and color depht 24 if you can.

But try to leave things as default if it's suggested.

Later after installing drivers you can alter it again.

Now we have to get you into gnome first.

When you're ready reconfiguring type startx.

If this won't work try```
sudo /etc/init.d/gdm restart
```

---

### Post by Kos-Mos on 2006-10-17
It only gives me the option of choosing a certain set of video modes. I tried several of them and its not fixing the problem. I tried once selecting all of them, then ones that seemed they should be the ones, and tried the default ones.

---

### Post by bulldog on 2006-10-17
What happens when youre done?

Did you startx?

Or even sudo gdm?

---

### Post by Kos-Mos on 2006-10-17
Ok, what I have been doing is starting up ubuntu, and doing the ctrl+alt+F1 to drop down to the command line, I then log in and use 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

to bring up the thing, I choose the video modes that I want, it then drops me back to the command line, where I use the

```

sudo /etc/init.d/gdm restart

```

command that puts me back to the scrambled screen with the new video mode that I selected.

I tried just typing in

startx

but it messed up, I believe my computer froze. I'll double check.

---

### Post by bulldog on 2006-10-17
Okay last thing I can think of.

Login on the command line and type,```
sudo aptitude install ubuntu-desktop
```

Maybe your desktop files are scrambled.

---

### Post by Kos-Mos on 2006-10-17
Well, when using the

```

sudo aptitude install ubuntu-desktop

```

command it did do something, it was going to install stuff but it held back a whole bunch of files and installed nothing.

The thing that happens when I use startx from the recovery mode command line is that it tells me that it cant display that video mode and that the optimum resolution is 1280x1024. I tried selecting that as my video mode and then using startx, still gave me the same message.

---

### Post by bulldog on 2006-10-17
> **Kos-Mos said:**
> Well, when using the

```

sudo aptitude install ubuntu-desktop

```

command it did do something, it was going to install stuff but it held back a whole bunch of files and installed nothing.

The thing that happens when I use startx from the recovery mode command line is that it tells me that it cant display that video mode and that the optimum resolution is 1280x1024. I tried selecting that as my video mode and then using startx, still gave me the same message.

Well I'm out of options.
It wouldn't reinstall ubuntu-desktop and held back a bunch.

I think a reinstall is the only option and check the live cd on errors before you do so.
There's an option in the startmenu.

There's something wrong and I can't figure out what it is,sorry.

---

### Post by Kos-Mos on 2006-10-17
Well, I will borrow a crappy computer from someone and make a video of what I am doing and put it on youtube. I am quite desperate lol.  I wont be able to do this probably until the end of the month.

For now, all I can do is take pictures and load them to a picture hosting site. I wont be able to do so for another hour or so because I am waiting for that person to bring the camera to me.

Thanks for the help btw.

EDIT:

I did check the disc for errors and none were found.

---

### Post by monktbd on 2006-10-17
what video card and monitor do you use?

maybe you can find some information to enter directly into the xorg.conf with googling for your hardware?

usually ubuntu is able to determine some correct video modes but for you it either could not or some files and libs are really broken.

does your internet connection work on the ubuntu machine? if you use a router with dhcp or just dhcp it might work already giving you the chance to do some updates on the command line that might fix it.

---

### Post by Kos-Mos on 2006-10-17
Video Card: NVIDIA GeForce 6800
Monitor: LCD

I dont know if ubuntu runs an internet connection or not x.x... This is my first time trying to use something besides windows.

---

### Post by monktbd on 2006-10-17
ok i guess you tried to use these settings already with reconfoguring the xserver. also i would do it now not from the recovery option but from the non working normal boot option and the login to the command line there.

i also would try a setting of 1024x768 60 hertz and color depth 16
and 1280 x 1024 60 hertz and color depth 16.

also it would be interesting what is listed in your xorg.conf for the device (although that should be listed while reconfiguring the xserver as well).

the xorg.conf can be read with

> nano /etc/xorg.conf

---

### Post by Kos-Mos on 2006-10-17
Currently windows is running at 1240x768x75 hertz. How do I specify my the color depth? I havent been able to do that yet.

Here is all my display info according to windows:

Name	NVIDIA GeForce 6800
PNP Device ID	PCI\VEN_10DE&DEV_00C1&SUBSYS_024510DE&REV_A2\4&1A646D2D&0&0008
Adapter Type	GeForce 6800, NVIDIA compatible
Adapter Description	NVIDIA GeForce 6800
Adapter RAM	256.00 MB (268,435,456 bytes)
Installed Drivers	nv4_disp.dll
Driver Version	6.14.10.7774
INF File	oem3.inf (nv4_overlay_OutputDevice_NV3x section)
Color Planes	1
Color Table Entries	4294967296
**Resolution	1024 x 768 x 75 hertz**
**Bits/Pixel	32**
Memory Address	0xFC000000-0xFEAFFFFF
Memory Address	0xE0000000-0xEFFFFFFF
Memory Address	0xFD000000-0xFDFFFFFF
IRQ Channel	IRQ 16
I/O Port	0x000003B0-0x000003BB
I/O Port	0x000003C0-0x000003DF
Memory Address	0xA0000-0xBFFFF
Driver	c:\windows\system32\drivers\nv4_mini.sys (6.14.10.7774, 3.05 MB (3,198,304 bytes), 10/15/2006 4:11 PM)

I just figured I would give that incase it could be useful in any way.

---

### Post by monktbd on 2006-10-17
> **Kos-Mos said:**
> Currently windows is running at 1240x768x75 hertz. How do I specify my the color depth? I havent been able to do that yet.

the color depth is actually written into the xorg.conf.
since i am behind a windows machine right now i cannot check how it exactly looks like while reconfiguring the xserver.

and copy/pasting the xorg.conf is also not really easy without having a proper gui :). thats why i recommended looking at it.

e.g.
[http://www.ubuntuforums.org/showthread.php?t=277385&highlight=xorg.conf](http://www.ubuntuforums.org/showthread.php?t=277385&highlight=xorg.conf)
you can see the different depths there.
i am not saying your xorg.conf should look like the above though :)

---

### Post by Kos-Mos on 2006-10-17
Well, I can't find the xorg.config file >_<. Also I have no idea what no idea what to do in nano. I tried doing a search for xorg.config in it, didnt find anything.

---

### Post by bulldog on 2006-10-17
```
sudo nano /etc/X11/xorg.conf
```
will bring it up.

---

### Post by Kos-Mos on 2006-10-17
EDIT:

I was wrong, it is quite similiar.

This is impossible =/

---

### Post by Kos-Mos on 2006-10-17
Ok, I got some pictures:

GrubMenu:
[http://img172.imageshack.us/my.php?image=grubmenuii5.gif](http://img172.imageshack.us/my.php?image=grubmenuii5.gif)

Ubuntu Startup:
[http://img241.imageshack.us/my.php?image=ubuntustartupbo0.gif](http://img241.imageshack.us/my.php?image=ubuntustartupbo0.gif)

Scramble Part 1:
[http://img134.imageshack.us/my.php?image=phase1scramblebd9.gif](http://img134.imageshack.us/my.php?image=phase1scramblebd9.gif)

Scramble Part 2:
[http://img228.imageshack.us/my.php?image=phase2scramblevn6.jpg](http://img228.imageshack.us/my.php?image=phase2scramblevn6.jpg)

thats basically what happens when booting up ubuntu. Scramble Part 1 flips into Scramble Part 2. When on Scramble Part 2, I can hit ctrl+alt+F1 to drop down to the command line to log in.

---

### Post by %hMa@?b&lt;C on 2006-10-17
login via commandline (by using ctrl alt f1) then try the 
"sudo dpkg-reconfigure -phigh xserver-xorg" command and see if that doesnt work.

---

### Post by Kos-Mos on 2006-10-17
woops forgot to add a picture of me doing that lol:

XServer:

[http://img140.imageshack.us/my.php?image=editxserverph4.gif](http://img140.imageshack.us/my.php?image=editxserverph4.gif)

EDIT:

If you want, I can go load up my xorg.conf file write it all down on paper, then write it all on here if you want lol. I am just about willing to do anything at this point xD

---

### Post by Kos-Mos on 2006-10-17
Well, I am making a little bit of progess. I managed to get the PC Desktop one to boot from. But, I get a scrambled screen at the same spot again.

Could this have to do with me having a 64-bit processor and trying to install a 32-bit OS? I have the 64-bit already downloaded, but never tried it yet.

I always thought a 64-bit had the option of running both.

EDIT:

I got the live cd to work by starting up with safe graphics ^_^... I am on it right now. I am going to attempt to install now.

---

### Post by monktbd on 2006-10-18
ok so i think for whatever reason the os cannot properly detect the correct settings for your video card/monitor combo.
i dont think the 64bit version will help, usually the 32bit ones are more stable and reliable up to now.

when reconfiguring the xserver try to select the vesa driver maybe it helps. if not go back to the nv driver.

i give you (a part) of my xorg.conf, but i have the closed source drivers from nvidia installed (thats why it says nvidia and not nv in the driver option).

```

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


Section "Monitor"
    Identifier     "BenQ FP71V+"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "BenQ FP71V+"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

```

i also found a thread pointing out the same problem:
[http://ubuntuforums.org/showthread.php?t=189752](http://ubuntuforums.org/showthread.php?t=189752)

also a link to his guide to install the nvidia closed source drivers, even without a working internet connection on the ubuntu box:
[guide](http://albertomilone.com/latest_nvidia_udsf.html#head-c2bea7ff8cf0ccc77693560b03eca86f427766ee)

---


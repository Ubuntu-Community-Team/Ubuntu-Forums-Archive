---
title: "error bcm43xx_microcode5.fw"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-04-08
Hi, I have an Ubuntu Ultimate Gamers Edition Live DVD and when I try to boot Ubuntu this shows up Failed to start the X server (your graphical interface)
It is more likely that it is not set up correctly. Would you like to view the X server to diagnose the problem. [17178756.068000]bcm43xx:Error:microcode
"bcm43xx_microcode5.fw" not available or load failed.
<Yes> <No>

When I click yes this shows up
Error:Microcode "bcm43xx_microcode5.fw" not
available or load failed. Version 7.11
Release date: 12 May 2006
Protocol version 11, Revision 0, Release 7.11.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri
Oct 13 18:45:35 UTC 2006 i686
Build date: 07 July 2006
or load failed. reporting problems, check [www.wiki.x.org](www.wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) Log File:/var/log/Xorg.0.log time: Mon Apr 2 19:24:36 2007
(==) Using config file: "/etc/X11?xorg.conf"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1)
found
(EE) I810 (0): No video BIOS modes for chosen depth.
(EE) Screen(s) found , but none have a usable configuration.
Fatal server error:
no screens found
This is a blue and white and red screen with lots of weird letters around that.

Then a black screen pops up:
firmware_helper [4970]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
for device '/class/firmware/000:0c:00.0' with driver 'bcm43xx'
[17179669.95200]bcm43xx: Error:Microcode "bcm43xx_microcode5.fw" not available
error load failed.
Do you know what I should do? I tried to disable the Wi-fi in BIOS, but that doesn't work. I have an Inspiron E1405. Will version 6.06 have the same problem?

---

### Post by rajeev1204 on 2007-04-09
Hi

Is this the first time u r installing or did the xserver recently fail? 

Anyways do this 

sudo dpkg-reconfigure xserver-xorg

This opens up a text based editor for your grphical (xserver ) setup .

Go through the options and see what happens .


regards
rajeev

---

### Post by mikecomua on 2007-04-09
Where should I type it?

---

### Post by gattung on 2007-04-22
I also am getting this error message but off of the new 7.04 CD. I am also on a dell 1505 (6400) with an ati x300 video card.

The funny thing is I can boot the 7.0 beta live cd just fine.

---

### Post by rm249 on 2007-04-23
I am also having the same problem, I have the EXACT same system as gattung.

---

### Post by rm249 on 2007-04-23
I would also like to add that I HAVE attempted to disable my wireless card in BIOS and then boot into Ubuntu, I thought this would have worked but it did not. I didn't have time to try to copy / write down what it said I will try to do that sometime tomorrow.

---

### Post by plum_sd on 2007-05-16
> **gattung said:**
> I also am getting this error message but off of the new 7.04 CD. I am also on a dell 1505 (6400) with an ati x300 video card.

The funny thing is I can boot the 7.0 beta live cd just fine.

I have the same problem on my Inspiron 6400 ?
Does anybody know how to solve this problem ?
tnx in advance

---

### Post by karobchip on 2007-07-07
I have the exact same error message with my Dell Inspiron 9400. Does anyone know of a solution?

---

### Post by zariuq on 2007-08-02
I have a very similar problem on a similar labtop...

(when I messed it up the first time it showed this while I was trying to fix it... even after reinstalling with a live usb (have no CD drive) thing it showed this once during bootup... then one time It logged me out with this error when a logged in (next morning) and I could only log in with root.
   after that shutdown I couldn't log in and this error came up...
I got logged in by mounting the .iso of the cd on my HDD and finding some dpkg xserver-xorg-blahblah.deb thing... next morning this didn't work either...  

would reinstalling work (although I don't have anything to do that with)...  I'm not sure how to proceed... along with others here...)

:(:confused::(

---

### Post by Aysilon on 2007-08-19
Hi to all!

I have the same problem on my Asus A6000 laptop.

here is the solution, that worked for me.

Run the Ubuntu from CD, go to Terminal and write:

rm /etc/X11/xorg.conf

Reboot the pc and should work.

---

### Post by toucher5 on 2007-08-20
I am receiving the same error as everyone here. I am using v7.04 of Ubuntu and I am using it on a Dell Inspiron 2200. I had 5.10 installed and just installed the new version in the free space after I resized with GPartED. I hope someone knows how to fix this.:confused:

---

### Post by likemindead on 2007-08-31
Looks like there's a long line of us and I'm joining in. Same problem here with my Acer Aspire 3003LCi. (Terrible hardware for Linux. Grrr.) :mad:

Anyone out there able to help all of us? :confused:

Thanks so much in advance.... :)

---

### Post by anewguy on 2007-08-31
The message is saying that at boot it is detecting a broadcom 4300 series wireless adaptor, and it can't find the firmware file for it.  This is because there is a default driver for that series but no firmware is provided.  The fix is to use ndiswrapper and load the Windows drivers for the wireless card.  I will point you to the how-to for my laptop - just follow the stuff in how to get the wireless working.  Check the link:

[http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215+how-to]("http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215+how-to")

I can't help you with the video but have seen it in the posts.  Try "Search" in the forum for the card/chipset.:)

---

### Post by likemindead on 2007-09-01
My computer is freezing up when I try to download and/or install necessary updates to run ndiswrapper. Grrr.....

Is there a way I can manually reinstall bcm43xx_microcode5.fw ?

Hoping....

---

### Post by likemindead on 2007-09-01
[SOLVED]

Everybody head over to this thread: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

[SOLVED]

---

### Post by anewguy on 2007-09-01
> **likemindead said:**
> My computer is freezing up when I try to download and/or install necessary updates to run ndiswrapper. Grrr.....

Is there a way I can manually reinstall bcm43xx_microcode5.fw ?

Hoping....

The problem is that there isn't any firmware available.  That's why most people choose the ndiswrapper way as it is eary to get to work.  

You can also try the firmware cutter and see if you can get it to work.  It wouldn't run on my machine.  Trying synaptics package manager and download bcm43xx-fwcutter.:)

---

### Post by Jeffrey Magder on 2007-09-13
I'm still working on the bcm43xx_microcode5.fw error message, and I will try the links provided above.  But I wanted to add that this is a separate problem from the Gnome Display Manager (gdm) failing to load.  

I was experiencing the same failing GDM problem during the installation of Feisty from the LiveCD, in this case on a Dell 1721 with an ATI Xpress 1270.  Though from the sounds of it I believe the underlying problem is the way the xorg.conf files are generated/used with most ATI mobility hardware.  At any rate I came across a solution at: 

[https://answers.launchpad.net/ubuntu/+question/8351](https://answers.launchpad.net/ubuntu/+question/8351)

To cut through the clutter, you need to [FONT="Courier New"]sudo vim /etc/X11/xorg.conf[/FONT], and search for the [FONT="Courier New"]Monitor[/FONT] entry.  On my system, the file was missing horizontal and vertical refresh rate configurations, so it was impossible to find a matching video mode.  You can provide this information by adding:

[FONT="Courier New"]
HorizSync 36-52
VertRefresh 36-60
[/FONT]

to the file.  Make sure to exit the original error screens, and then run:

[FONT="Fixedsys"]sudo /etc/init.d/gdm restart[/FONT]

Its important you exit all original error screens, or the restart won't work.  Note that the numbers provided above should be compatible with most hardware.  You can obviously use more optimal settings for your hardware, but that should really matter for the purposes of the install. :-)

I hope this helps.  Good luck!

---


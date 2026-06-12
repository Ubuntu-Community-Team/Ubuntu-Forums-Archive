---
title: "Used Unetbootin to install ubuntu - hear sound but no image"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by rcfuller on 2008-04-08
Warning - linux newbiew - Warning :)

I have a Dell Smartstep 100N with 384 MB Ram and an intel 82830M graphics card, 20 GB Harddrive, celeron 1.4 Ghz? Processor

I have "played" around in ubuntu desktop before (on someone elses machine) and liked it and wanted to play with it. A dual-boot option sounded great to me, and I did my research, found netbootin, successfully installed netbootin, pulled in ubuntu desktop, and all seemed good.

First time to boot into ubuntu, I got only dark screens - i heard the "african drumbeat", but no gui :(
second time, I got the white screen with vertical lines on the right side - still not accessible

I did some looking, read about the sudo dpkg-reconfigure xserver-xorg command and have tried a series of changes to the graphics setting to no avail. 

I have run netbootin again, wiped the first install - same results. Any help/suggestion would be appreciated. I am a TOTAL command line newbie, so I need step-by-step!

RFuller

---

### Post by dstew on 2008-04-08
Can you get a command-line interface if you boot into Recovery Mode, or if you press ctrl-alt-F1? I guess so, because you tried to reconfigure the xserver.

When you get to the command line, enter```
dmesg
```That will show the latest kernel messages. You can also look at the xserver log files in /var/log directory, to see what errors you are getting. I think the file name is Xorg.0.log or something like that. To list the log directory, use```
ls -l /var/log
```You can display it with ```
cat /var/log/Xorg.0.log
```Again, check the file name first, I am not at my Linux computer, so I am not sure that is the name. Post the errors you find.

---

### Post by rcfuller on 2008-04-09
Thanks for the reply - I did go through and look at the errors - once again, I am a newbie, but nothing looked out of the ordinary. I can't post them, because they are on the computer that won't behave...

Latest update:
Used the alternate cd to load ubuntu. Went very smoothly. When I boot to 7.10, i hear the drum beat, but it is still a blank screen. If I ctrl-alt-f1, i see login: then password: but they are in VERY LARGE LETTERS. I have tried the intel driver with 1024x768 60mHz and vesa with the same result. In my very unexpert opinion, it seems as if I need to know which driver to pick. The Service Tag for my dell is CBNDL01

I have read various posts about the 82830m graphics chipset, but no definitive answers. If I need to download additional drivers, please give me step-by-step - I am a command line newbie (although I just read what sudo means...)

Ryan

---

### Post by dstew on 2008-04-09
You went through dpkg-reconfigure xserver-xorg and chose the vesa driver, correct? Did you get a graphical interface when you did ctrl-alt-backspace?

---

### Post by rcfuller on 2008-04-09
No - just text, but it was LARGE TEXT - Have yet to see the graphical interface.
Ryan

---

### Post by dstew on 2008-04-09
When you first boot, do you get a grub menu? Is it normal sized? And, do you get a normal-looking Ubuntu splash screen? How about if you boot in Recovery Mode?

---

### Post by rcfuller on 2008-04-12
I get the grub screen with no problems - normal text size, etc. 

I have never seen the splash screen - but I do hear the drumbeat. If I hit Alt-CTRL-F1, I get a screen with LOGIN: in 640x480 (I am guessing..)

I recovery mode - everything comes up normally and I end up with the command line : root$!:

---

### Post by dstew on 2008-04-12
> I recovery mode - everything comes up normally and I end up with the command line : root$!:From the recovery code command line, do```
more /etc/X11/xorg.conf
```You step through the file using the spacebar, and press 'q' to quit. Look at the Section Device that is about your display. What is listed there?

---

### Post by rcfuller on 2008-04-15
This is what is chosen by default:

Identifier: Intel Corporation 82830 cgc
Driver: intel
BusID PCI:0:2:2

Monitor
Generic Monitor
Option: DPMS
HorizSync: 28-49
VertSync: 43-72

Screen
Default Screen
Device: Intel 82830
Monitor: Generic Monitor
DefaultDepth: 24

Thanks again for helping me through this...

---

### Post by 1875 on 2008-04-15
Have you tried rmoving the splash and quiet kernel options from /boot/grub/menu.lst ?

---

### Post by a.v.l on 2008-04-15
When you install the Ubuntu CD and get to the blue screen press F4 for VGA and select you monitor size before installing the operating system, worked for me.


> **rcfuller said:**
> Warning - linux newbiew - Warning :)

I have a Dell Smartstep 100N with 384 MB Ram and an intel 82830M graphics card, 20 GB Harddrive, celeron 1.4 Ghz? Processor

I have "played" around in ubuntu desktop before (on someone elses machine) and liked it and wanted to play with it. A dual-boot option sounded great to me, and I did my research, found netbootin, successfully installed netbootin, pulled in ubuntu desktop, and all seemed good.

First time to boot into ubuntu, I got only dark screens - i heard the "african drumbeat", but no gui :(
second time, I got the white screen with vertical lines on the right side - still not accessible

I did some looking, read about the sudo dpkg-reconfigure xserver-xorg command and have tried a series of changes to the graphics setting to no avail. 

I have run netbootin again, wiped the first install - same results. Any help/suggestion would be appreciated. I am a TOTAL command line newbie, so I need step-by-step!

RFuller

---

### Post by dstew on 2008-04-15
> This is what is chosen by default:I think the default settings are not working for you. You should try to use the vesa driver instead of the intel driver for the display. You do this by booting in recovery mode, and on the command line doing ```
sudo dpkg-reconfigure xserver-xorg
```Make sure you select the **vesa** driver when you get to the display part. Go all the way to end of the reconfiguration program, until you get back to the command line. Then do```
startx
```to start the graphical interface. If it doesn't work, go back the the command line, and look at your /etc/X11/xorg.conf file again. If it does not have the vesa driver in the display device section, something is wrong. You need to make sure you have tried the vesa driver before you give up.

---

### Post by stolle on 2008-05-13
i am having the same exact issue same laptop anyone else have any ideas? i have tried pretty much everything listed here...

---


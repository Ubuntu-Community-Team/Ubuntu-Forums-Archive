---
title: "Help! Installed Ubuntu 7.04 and it boots to comand line"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Erix18 on 2007-05-13
I installed Ubuntu from the live cd onto a machine running xp wipping out the xp partition. when i rebooted ubuntu booted onto the comand line.

---

### Post by bobplano on 2007-05-13
does it say something about X? if it doesn't you most likely installed the server edition and need to get a GUI
```
sudo aptitude install ubuntu-desktop
```
if it says X didn't start post your graphics card

---

### Post by Erix18 on 2007-05-13
k im almost sure i installed the desktop version and i got the message  
/bin/sh: sudo: not found 
also before the comand line starts i get this message
Udevd-event[1934] run_program '/sbin/modprobe abnormal exit

---

### Post by bobplano on 2007-05-13
did you check the cd for errors before you installed? also  check the md5sum of the .iso you downloaded

---

### Post by Erix18 on 2007-05-13
what is the md5sum supposed to be

---

### Post by bobplano on 2007-05-13
all the sums are here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
for the 64-bit fiesty: a2b159599b69cea51371eee1ec5feda6
for 32-bit: e296e3468358789904097fc8df29609a
if you don't know how to check the sums go [here]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by Erix18 on 2007-05-13
and no errors were found on the disk

---

### Post by Erix18 on 2007-05-13
yah theyr right

---

### Post by bobplano on 2007-05-13
does it go straight to the command line or does it have some errors about X?

---

### Post by Nekiruhs on 2007-05-13
Try sudo /init.d/gdm start

---

### Post by Erix18 on 2007-05-13
no erors about X but first it says
Udevd-event[1934] run_program '/sbin/modprobe abnormal exit
then it says Busy Box v1.1.3 and goes on aboutdemean and stuff and says type help for a list of comands 
but it boots to  the live cd without erorrs

---

### Post by bobplano on 2007-05-13
yea go ahead and try the command from Nekiruhs. then maybe try pressing ctrl+alt+F7. i don't think that will work but might as well give that a try. you might also try:
```
sudo dpkg-reconfigure xserver-xorg
``` and answering the questions as well as you can.

---

### Post by Erix18 on 2007-05-13
.

---

### Post by Erix18 on 2007-05-13
ok i typed in the first string and it said sudo not found the i typed it in againn and pressed ctl alt f7 and nothing happened so i pressed it again and the screen went blank ith a little beeping line ( i might have hit f6)
im restarting wich also takes a long time for some reason

---

### Post by bobplano on 2007-05-13
have you tried recovery mode or an older kernel? it sounds like you aren't really in a terminal, there's something else that it might boot into that doesn't have the usual commands, and it sounds like that's what your in.

---

### Post by Erix18 on 2007-05-13
ok im trying recovery mode but what should i do from there and this is a new install

---

### Post by bobplano on 2007-05-13
well if it boots up into that command line where it says type help for commands i have no clue how to fix that. otherwise if you have at least a terminal than try using the sudo dpkg command as that will fix your xorg. but it sounds like you have problems other than your X

---

### Post by Erix18 on 2007-05-13
ok so after what i think is the comand line opens there is another error message saying jobs could not load or was disabled or something i dont really know im turning it on again to comfirm

---

### Post by Nekiruhs on 2007-05-13
> **Erix18 said:**
> ok im trying recovery mode but what should i do from there and this is a new install
Once you get into recovery mode try the commands that bobplano and I offered (His will more likely do i than mine).

---

### Post by Erix18 on 2007-05-14
whats recoevry mode supposed to look like i get a bunch of line of code and then i t all just stops
edit 
now it says starting shell b/c (something) was not found

---

### Post by Erix18 on 2007-05-14
uh this sucks i feel like  im trying to install vista

---

### Post by bobplano on 2007-05-14
if this is a fresh install then why not try reinstalling? something seems wrong with this install if it keeps going to the shell if that's what it really is called, where you don't have commands like sudo. if you do have important info on there for whatever reason just back those up and reinstall

---

### Post by Erix18 on 2007-05-14
i did reinstall b4 posting this whole thing the first time i tries to install it did not work and gave a message that the installer could not partition the hard drive corectly or something si i tried again and got the shell so then i reinstalled again and got the shell again

---

### Post by pikul on 2007-05-14
When you try to re-install, do you try to format the disk first or just start the installation? it would be a good choice to format your disk first with Gparted, and then begin installation, you can check your cd with the tool that the live cd disk has to rule out a wrong cd.

---

### Post by Erix18 on 2007-05-14
No i just started the installation because the first time i did it it had trouble partioning/formating the disk so i was just happy it worked and didnt try to format it

---

### Post by SeaWolf on 2007-05-15
Hi Erix18-

Your problem isn't common, but it's been seen in other places.  I'm also suffering from it.  The suggestions below assume that the hard drive does not contain information, or operating systems that you wish to keep.  To start, disconnect every USB device that you can from your computer.  Next do a re-install from the LiveCD and let the system partition the drive the way it wants to.  Once the install is complete, reboot and hopefully everything will come up OK.  At this point, plug one USB device in and reboot.  Repeat as many times as needed to plug in all of your USB devices.  If it locks up while plugging in the USB devices, try a reboot to see if it clears the problem.

This is how I finally got Feisty installed on my Asus P4S333-VM motherboard but the nvidia driver was causing problems, so I'm back to looking at this problem

---


---
title: "Ubuntu on Macbook Pro 7,1 / 7.1 mid 2010"
date: 2014-10-11
forum: Apple Hardware Users
---

### Post by christian44 on 2014-10-11
Hi everybody,

i have decided to try to switch to linux, maverick is getting slow. I already bought a ssd, but a half year later, it's getting slower and slower. So i would like to install ubuntu.
I already downloaded a few images of and created a bootable usb stick with "unetbootin" on osx. But my problem is that the stick is not showing up in the startup when i hold the option-key.

I started with Ubuntu 10.10: [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

Then i tried Ubuntu 11.10 and after that the current version, 14.04 : same problem, not showing up in startup. I formatted the stick everytime with FAT and installed the images with "unetbootin".

Am i doing something wrong?

Or maybe someone can give me a hint or help to get ubuntu run on my macbook. 

I already thinked about sell the macbook and getting a thinkpad, but i don't want to miss the big multitouchpad of the macbook. So this is no option for me. 

Hope some of you can help me with this...

... and sorry for my english if something's not perfect :)

---

### Post by christian44 on 2014-10-11
I tried to create the stick on a dell laptop with xubuntu 14.04 installed...and i installed Ubuntu 14.04 finally on my macbook. BUT: The splash screen is full of pixels and not really desigtned:

Something like this here: [http://www.upload.ee/image/2410443/IMG_20120608_012957.jpg](http://www.upload.ee/image/2410443/IMG_20120608_012957.jpg) (but just with the colors white and ubuntu orange).

The second thing, are missing letters in words. for example lo out or s ttings, they are just not displayed. So i thought let's just do the following to upgrade and get the newest graphics driver:
```

sudo apt-get update

sudo apt-get upgrade

```

Reboot the system and now i have a black screen. I tried to get into boot-menu to start the recovery-mode but it just don't work.
What can i do now? Re-Install Ubuntu?

---

### Post by este.el.paz on 2014-10-11
> **christian44 said:**
> I tried to create the stick on a dell laptop with xubuntu 14.04 installed...and i installed Ubuntu 14.04 finally on my macbook. BUT: The splash screen is full of pixels and not really desigtned:

Something like this here: [http://www.upload.ee/image/2410443/IMG_20120608_012957.jpg](http://www.upload.ee/image/2410443/IMG_20120608_012957.jpg) (but just with the colors white and ubuntu orange).

The second thing, are missing letters in words. for example lo out or s ttings, they are just not displayed. So i thought let's just do the following to upgrade and get the newest graphics driver:
```

sudo apt-get update

sudo apt-get upgrade

```

Reboot the system and now i have a black screen. I tried to get into boot-menu to start the recovery-mode but it just don't work.
What can i do now? Re-Install Ubuntu?

@christian:

I believe I have about the same MBPro as you do . . . one of the problems is unetbootin has traditionally not been supported by OSX . . . so if you got your USB stick made in windows or ubuntu that should be OK.  Did you check the md5sum number of the iso before you made the stick?  If it isn't correct you can get errors in your install.  Also, did you run the "live desktop" in your MBPro before you did the install?  Did the "live" version run OK on your computer?

Also, the general wisdom is to do a "dual boot" system, keeping OSX as the base system in the first partition.  Anyway, let's say the md5sum number is OK . . . and perhaps the install is OK, but you have black screen.  Did you try to boot the install with "SuperGrub 2" ????  See if that gets you into a viable system.

If not, if you still have OSX, add "rEFInd" to the system, then reinstall . . . I prefer Xubuntu for our computer . . . if you can set the space you want for linux to "free space" in GParted installer, then try to run "install into largest free space" . . . after the install **shut the computer down" . . . then on reboot, select linux and see if you can get in.  If you can . . . try to add the Nvidia drivers from "Software Updater" . . . .  

If that doesn't work, use "manual" install and set aside 10MB flagged as "bios_grub" . . . then the "home" flagged as "/" and set as "ext4" . . . and then "swap" at 1 - 2x RAM . . . .  Again, shut down after the install and then cold restart.

e.e.p.

---


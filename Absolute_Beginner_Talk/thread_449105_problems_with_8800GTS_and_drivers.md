---
title: "problems with 8800GTS and drivers"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by zomw on 2007-05-19
I have recently been trying to install the nvidia drivers on feisty that support the 8800 cards.  I have tried all of the methods I could find on these forums and none of them worked.  All of them resulted in an xserver crash.  I have also already tried the envy script.  I read one of the xserver crash logs, and it said something about an nvidia card not being found (as stated in the title, I have an 8800GTS).  The card works fine in both XP and Vista.

Can anyone help me resolve this? 

P.S. - I have already reinstalled feisty two times because of this, so doing that probably won't help.

---

### Post by Bachstelze on 2007-05-19
Without knowing exactly hat you've done, it will be hard for us to tell you what you did wrong. All you should need is

```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig
```

and restart your X.

---

### Post by zomw on 2007-05-19
I tried that and X crashed again upon reboot.  
Here is exactly what it says afterwards:

"API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9755. Please make sure that the kernel module and all NVIDIA driver components have the same version."

Do I have to update the NVIDIA kernel module? And if so, how do I?

---

### Post by Bachstelze on 2007-05-19
The previous attempts you made to install the drivers certainly messed your setup up a bit. Can you afford a reinstall ?

---

### Post by zomw on 2007-05-19
Ok, so I reinstalled feisty again just to be sure and X crashed again after executing the commands you gave me.

Here is the output:
```
Failed to load module "wfb" (module does not exist, 0)

NVIDIA (0): Need libwfb but wfbScreenInit not found

Fatal server error:
AddScreen/ScreenInit failed for driver 0

```

---

### Post by Bachstelze on 2007-05-19
Ubuntu being stupid once again. The driver needs libwfb.so but there is no Ubuntu package for it. Just give up on Ubuntu packages and use the installer from nvidia.com :)

---

### Post by zomw on 2007-05-20
Could you give me a link to that? Don't want to download the wrong one ;)

---

### Post by Bachstelze on 2007-05-20
[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

save it for example on your desktop and do

```
sudo apt-get remove nvidia* linux-restricted-modules*
sudo apt-get install linux-headers-$(uname -r) build-essential pkg-config xorg-dev
sudo sh ~/Desktop/NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

(last line assuming you saved it on your desktop, adapt to the correct location if you didn't)

---

### Post by zomw on 2007-05-20
After executing those commands X crashed again :(

Output:
```
sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia
(EE) NVIDIA (0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA (0):     ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.


Fatal server error:
no screens found

```

---

### Post by Bachstelze on 2007-05-20
And Ubuntu is being stupid once again... When if forces you to do things The Ubuntu Way (TM), you'd at least expect it to work... Can't help you further, I'm afraid, maybe wait for someone else ?

---

### Post by zomw on 2007-05-20
Thanks for your help anyway:)

Anyone else?

---

### Post by Hobo Joe on 2007-05-20
Have you tried [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

Worked first time for my 8800 GTS, so it *should* work for yours!

---

### Post by zomw on 2007-05-20
I just tried envy for the second time and it did not work (x crashed again).  

Output:
```
sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia
(EE) NVIDIA (0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA (0):     ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.


Fatal server error:
no screens found

```

---

### Post by zomw on 2007-05-20
Anyone?

---

### Post by zomw on 2007-05-20
bump

---

### Post by heldal on 2007-05-20
This is probably due to a missing module (WFB) for the X-server in Ubuntu's nvidia-glx-new driver package. Check /var/log/Xorg.0.log to verify.
 I recently upgraded a video-card from a 6800 to a 8800gts. nvidia-glx-new worked with the 6800-card, but the machine locked up completely when starting X on the 8800. Manual installation of the missing X-server module fixed the problem here:

In case of a lockup start by booting with the recovery-image. (currently it seems to be missing some raid-stuff so ppl with their root fs on software-raid may have to use the default image and use grub to edit the kernel options to add a "S" and maybe remove "quiet" and "splash" to get screen output). Enter root-password for maintenance-mode (single-user mode).

Go grab nvidia's latest driver. It's currently the same version as the one included with feisty so there's no conflict:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

Extract the module source (note -x option):
```
sh NVIDIA-Linux-x86-1.0-9755-pkg1 -x
```

Copy the missing module:
```
cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules/libwfb.so
```

Remove the extracted driver source:
```
rm -rf NVIDIA-Linux-x86-1.0-9755-pkg1
```

Reboot.

---

### Post by Bachstelze on 2007-05-20
Instead of 

```
cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules/libwfb.so
```

do

```
cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules
cd /usr/lib/xorg/modules
sudo ln -s libnvidia-wfb.so.1.0.9755 libwfb.so
```

This is not specific to this but general *nix practice you should follow : *.so files should never be actual files but symlinks to them.


EDIT : And on my system, I even have libnvidia-wfb.so.1 as a symlink to libnvidia-wfb.so.1.0.9755 and then libwfb.so as a symlink to libnvidia-wfb.so.1

---

### Post by zomw on 2007-05-20
Thanks for the response heldal, but I need to clarify a few things since I am so new to linux.  First, does booting with the recovery image mean booting into the recovery mode in grub?  Second, doesn't the recovery mode automatically start under the root account (why would I have to enter the password?)?  Lastly, how do you know if you are in maintenance mode?

---

### Post by zomw on 2007-05-20
bump

---

### Post by zomw on 2007-05-21
Heldal, I assumed a few things and your method seems to have worked.  My xorg.conf file now says nvidia instead of nv for the device driver, and x did not crash on me this time.  

Thanks everyone!:D

---

### Post by DUNC4N on 2007-05-21
Would this work with the 64bit version?

I've been messing with this for days...

Thanks.

---

### Post by lhuser on 2007-05-21
The 64-bit version has the same functioning as the 32-bit. It's just programmed into a 64-bit interface. Nothing to worry on.

---

### Post by heldal on 2007-05-21
> **zomw said:**
> Thanks for the response heldal, but I need to clarify a few things since I am so new to linux.  First, does booting with the recovery image mean booting into the recovery mode in grub?  Second, doesn't the recovery mode automatically start under the root account (why would I have to enter the password?)?  Lastly, how do you know if you are in maintenance mode?

The easiest way to get into single-user mode (by some called "recovery mode", or even "maintenance mode") is to choose the prepared recovery-image in grub at boottime. Normally that works. You know you're in single-user because the machine stops and asks you to enter the root password for maintenance before it has started any processes related to multi-user operation.

Ubuntu is configured to ask the user to enter the root-password to get into single-user mode or ctrl-d to proceed to multi-user.

The failure mode I got into meant that the machine would crash when trying to start X. The installation of the missing file can also be done (as root, or prepending the commands with "sudo") in multi-user if the machine has survived its attempt to start X. In this case you shouldn't even have to do more than "/etc/init.d/gdm restart" to get X going once the missing file is in place.

PS! HymnToLife: I simply didn't care to bother with the normal symlinks for shared-lib versions because the affected file and links will have to be permanently sorted in a revised nvidia-glx-new package later.

---

### Post by DUNC4N on 2007-05-21
Big Thanks Heldal, finally got the drivers installed for my 8800gts:D

Finally...

---

### Post by funkengruven on 2007-06-06
Unforunately i am faced with a similar problem. i have the 8800GTS and installed the driver, kernel module, etc. In normal mode it boots to a black screen, in recovery mode it boots but once you go to run X it goes to an Nvidia splash screen and freezes completely. cannot go to console at all from there.

It did the same thing with Gentoo and Debian with this driver. Any ideas?

---

### Post by CaptainInsaneO on 2007-07-04
Heldal, I could kiss you!!

Brand new 8800gts, and I thought it was a 300 dollar paperweight, along with a borked Feisty install.

Your fix worked wonders!!

---


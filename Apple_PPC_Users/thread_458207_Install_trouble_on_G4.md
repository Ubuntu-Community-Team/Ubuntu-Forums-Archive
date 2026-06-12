---
title: "Install trouble on G4"
date: 2007-05-29
forum: Apple PPC Users
---

### Post by mrhardin on 2007-05-29
I'm trying to install 7.04 on a Mac G4 and can boot to the CD.  The problem is somewhere in the install process I think.  I get to the screen that says "Ubuntu" with a progress bar but the colors look off (very rainbow-y in an 8-bit way) and the progress bar is not moving.

I'm a total noob so please be kind and help.  I'd like to try this Ubuntu thing:D

---

### Post by stmiller on 2007-05-29
Hey we can help! What model of mac do you have specifically? Look on [www.apple-history.com](www.apple-history.com) if you aren't exactly sure.

Some have issues with the live CD, but there are workarounds.

---

### Post by mrhardin on 2007-05-30
Thanks.  Here's the lowdown:

I'm installing Kubuntu 7.04

Mac is:
867 MHz PPC G4 (2.1)
2MB L3 Cache
1.12 GB SDRAM

Nvidia GeFroce2 MX in AGP slot (32MB)

Pioneer DVD-RW  DVR-103

and if it matters it's currently running OSX 10.3.2

Thanks again.

---

### Post by tcrroadie on 2007-05-30
Hi mrhardin,

Since you said that your display is freezing during boot before the log in screen comes up, you may have one of a few problems.  

First, do you ever hear the drums beat?  When the log in screen (GDM) comes up, you will hear some drums.  

If your system is simply freezing, you may have a faulty cd or you may have a bad ram module.  

The Ubuntu live disk includes a memory test function.  The memory test is included in one of the boot options on the cd.  You may want to run it to test your ram modules.

---

### Post by mrhardin on 2007-05-30
I never hear any drums.  Here's the process:

Restart.  Hold down "c".  Hear Mac chime.  Boot screen comes up.  I hit "enter" and colorful Kubuntu screen comes up with a progress bar.  The indicator only gets about 80 percent to the right then freezes.  If I type "live video=ofonly", I get a little farther in that the indicator goes back and forth about 3x then freezes.

---

### Post by stmiller on 2007-05-30
Hm, may have to install with the alternate PPC CD. Same as the Live CD, but just goes right to the installer and skips the pretty live desktop.

---

### Post by mrhardin on 2007-05-30
I'm downloading the alternate now and will report back.  Thanks for all the input so far.

---

### Post by tcrroadie on 2007-05-30
You may also want to try specifying the video driver used during boot.  You can pass a boot option to select the video driver used when booting the live cd.  Try one of these two boot options.

xdriver=vesa 

xdriver=nv

---

### Post by Radim on 2007-06-07
I've got exactly the same computer and exactly the same problem. I tried many different distributions such as openSuse 10.2, Fedora 7, Yellow Dog 5.0.1, and of course the new Ubuntu 7.04 which I manage to get the installation process farthest (in my opinion). I tried connect the keyboard directly to the computer and not using the USB hub in the screen.
One more option which I'm going to try is not using Studio Display screen, but just a normal screen. I'll report the progress later.

---


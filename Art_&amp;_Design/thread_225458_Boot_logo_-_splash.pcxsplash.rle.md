---
title: "Boot logo - splash.pcx/splash.rle"
date: 2006-07-29
forum: Art &amp; Design
---

### Post by lolipop on 2006-07-29
Hi there,

I don't know if i'm posting in the good section because it's not really "art". So if I mistook please move this thread where you want. :)

I'm trying to customize an ubuntu and I would like to modify the boot logo. When I search in the cd I found that logo in "isolinux/splash.pcx". In the file "isolinux/isolinux.txt" we can find what is displayed at te boot, and for the logo it's the file "splash.rle".

However if I can modify the .pcx with Gimp I'm not able to do that for the .rle. So if I change the .pcx I won't see the differences because the "isolinux.txt" file calls the "splash.rle" file.

So my question is : how can I apply the modifications that I did on the .pcx to the .rle ?

If you have other questions I'll be pleased to answer them. :D

Thanks in advance. :]

---

### Post by d1gital on 2007-01-04
I have the same question.  Someone please reply!  
                                                                               Thanks,
                                                                               -digital

---

### Post by Steve S. on 2007-01-12
> **lolipop said:**
> Hi there,

I don't know if i'm posting in the good section because it's not really "art". So if I mistook please move this thread where you want. :)

I'm trying to customize an ubuntu and I would like to modify the boot logo. When I search in the cd I found that logo in "isolinux/splash.pcx". In the file "isolinux/isolinux.txt" we can find what is displayed at te boot, and for the logo it's the file "splash.rle".

However if I can modify the .pcx with Gimp I'm not able to do that for the .rle. So if I change the .pcx I won't see the differences because the "isolinux.txt" file calls the "splash.rle" file.

So my question is : how can I apply the modifications that I did on the .pcx to the .rle ?

If you have other questions I'll be pleased to answer them. :D

Thanks in advance. :]

Did you get this solved yet?  If not, please clarify: are you trying to modify the usplash boot up screen?  Are you trying to modify for a livecd, or an already installed version?

---

### Post by otakonx on 2007-02-06
I'm having close to the same problem. Clean Edgy install on my Dell Optiplex.  When booting and shutting down I get a blinking underscore with a black screen.  On my other Dell (dimension) I get a nice loading bar with the Ubuntu logo. Any idea how I can get this on my Optiplex? 

Thanks!

note: I've tried doing the grub usplash update but that just got me a background for selecting the os before boot.

Otakonx

---

### Post by Steve S. on 2007-02-07
Well, I worked out some of the kinks in [Edgy usplash here]("http://www.ubuntuforums.org/showthread.php?t=323520")...note the end of the thread where I started to figure out what was going on.

And [in this thread ]("http://www.ubuntuforums.org/showthread.php?t=334428")I set up a custom Usplash.

Perhaps one of these will help and give you the information that you are looking for.

Please post back if it helps or not. :)

---

### Post by ff9will on 2007-09-21
Using Gimp, turn RGB into indexed (16 colours)
[[IMG]http://img503.imageshack.us/img503/4950/capturadatelaxu4.th.png[/IMG]](http://img503.imageshack.us/my.php?image=capturadatelaxu4.png)
And save as .bmp (rle coded) and change .bmp extension to .rle

---

### Post by ingo on 2008-04-21
Okay, so this thread might be dead, but in case anybody is interested:

You need to install syslinux in case you haven't got it.

1. create a new splash.png file (using gimp or whatever)

2. convert it to "pnm" by using "pngtopnm" as in 
> pngtopnm splash.png > splash.pnm

3. convert it to "rle" by using "ppmtolss16" as in
     > ppmtolss16 "#000000=0" "#ffffff=7" < splash.pnm > splash.rleBINGO!

---

### Post by ch1c0dj on 2008-04-25
With regards to ubuntu splash screen, what I do not like is the metering something or orange line that grows from left to right and vice versa because it resembles the Windows operating system boot screen.

I hope this will be remove or change to something unique that Ubuntu will be recognized of, and will be implemented on next Ubuntu release.

click the link to see
[Windows XP Splash Screen]("http://www.simplyguides.net/images/guides/convert_fs_ntfs/6.jpg")

[Ubuntu 8.04 Splash Screen]("http://decoding.files.wordpress.com/2007/04/boot-screen.jpg")

Attached is the part of splash screen from windows xp and ubuntu 8.04

---

### Post by smartboyathome on 2008-04-25
This is what looks best without Splashy, imo.

---

### Post by ingo on 2008-04-26
Please note that this is only for the boot splash, i.e. if you press esc to boot a different kernel for example. Otherwise you will not see the boot splash under Ubuntu. 

The last two posts, afaict, are musing over the image incl. the bar once the kernel has been selected and is booting. In Ubuntu usplash now takes over - splashy being the flash and up and coming alternative used by "prettier" systems.

Imo one should get rid of the splash boot option under grub and watch the messages flash by as the system comes up ;)

---


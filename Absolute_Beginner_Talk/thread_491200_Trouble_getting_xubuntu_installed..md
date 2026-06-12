---
title: "Trouble getting xubuntu installed."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by tobak30 on 2007-07-03
As i have understood xubuntu is a derivate off ubuntu. And has the same functions. But i have serious truble installing it onto my computer. I wanna have the xubuntu on my 40Gb hard drive. But is seems impossible for it to make the 3ext file system work. I get an error message every time. I have tried without luck with gparted to get new partitions on my disk. but that also failed. giving me a red warning sign by the partition i tried to "fix". I have also tried fdisk to no prevail. Maby i did something wrong there. I have managed to delete my windows. The file system under windows was fat32 i believe. But that is long gone now as i have messed about the whole day trying to fix the trouble. I am pretty noob with all this linux stuff so a step by step guide would be nice as dim folks like me can follow with.

---

### Post by thornomad on 2007-07-03
[QUOTE=tobak30;2955904]I get an error message every time.QUOTE]

What is the error message you are getting?  

And, you are correct: Xubuntu is a flavor of ubuntu that uses XFCE ... did you try to install the regular ubuntu and it worked and Xubuntu won't?

---

### Post by tobak30 on 2007-07-03
My first error message was:

The instalation application must store the necessary changes in the partition tablet. But couldn't do it cause it couldn't unmount

/media/System\040disk

Please close all applications who uses those mount points.

This is roughly translated from Norwegian as i am Norwegian. :)

The second error message i got is:

Couldn't make ext3 file system on partition #1 on IDE master (fda)

Haven't tried ubuntu on my computer as i am after speed on my old rig. Tired of windows bogging me down and stalling and all that security things. Windows makes me paranoid.


Hope this help.

---

### Post by thornomad on 2007-07-03
Are you using the LiveCD (Desktop CD) for your installation ?  Are you customizing the installation in any way or having Xubuntu completely erase the hard drive ?

I can think of a few things to try (I don't know what the problem is specifically, to be honest):

1. try using the alternate CD (you would have to download it);
2. try doing the default installation, if you are doing a custom one;
3. try doing a custom installation, if you are doing a default one;
4. download and attempt to use the gparted (which is what ubuntu uses) LiveCD to partition your hard drives BEFORE installing Xubuntu: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Those are my ideas.

---

### Post by tobak30 on 2007-07-03
Alternate cd? You mean the ubuntu live cd?

I am currently using the xubuntu live cd and xubuntu has gparted. I think i mentioned that one in a post further up.

I am trying to delete the entire hard drive to free some space and to get rid of windows.

I have tried to install it as default and custom and all that things you have mentioned. I have tried maybe 8 times today to install this thing. But still the 3ext won't be made. The hard drive i had windows on is now deleted according to gparted.

---

### Post by Rocket2DMn on 2007-07-03
The alternate cd is NOT the ubuntu live cd.  At the download page, the alternate CD is an option.  This will give you a text-based install disc.  Though I've never used it, everybody who uses it seems to be able to navigate it OK, so don't freak out about the lack of a graphical install.
[http://www.xubuntu.org/get](http://www.xubuntu.org/get) - select your mirror and choose the Alternate CD instead of Desktop.

---

### Post by sad_iq on 2007-07-03
Do what **thornomad** said and download the gparted live cd(it's small sized...don't worry)...you can use it to repartition your drive...exit it then install xubuntu onto the newly formatted drive.
 If the error message appears again(when using gparted live cd)...try formatting as reiserfs, or xfs, or jfs then if the error dissapears reformat as ext3. 
 Also when you boot the xubuntu live cd the drive will get mounted and it will not allow you to format it(could be wrong thou)...just right click it and select unmount!!! 
 Also there are 2 types of xubuntu cd's(well more...but you can only use 2)...Xubuntu LiveCd and Xubuntu Alternate. The Alternate is for systems that are low in hardware specs(usualy ram) and can't boot of the LiveCd...thus can't install...and the Alternate will give them a way to install (XKEdu)Ubuntu in a text mode!!!

---

### Post by PhilJ on 2007-07-03
I had problems with the file manager popping up and the install stopping when trying to make the file system. I found the answer by unmounting the hard disc in the file manager and then the install continued ok

Philj

---

### Post by bapoumba on 2007-07-03
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
Here is the link to get the alternate CD.
I choose text install mode (I think, or close ^^). At the end, there is no GUI, and network should be set up (what kind of netword card do you have?).
I installed xubuntu-desktop, and rebooted.

---

### Post by Rocket2DMn on 2007-07-03
FYI: using the link bapoumba has provided for you gives you the Ubuntu alternate install cd (not Xubuntu), but once you everything loaded, installing "xubuntu-desktop" and setting that as your default login session will basically have you using xubuntu (the Xfce environment rather than Gnome).
```
sudo apt-get install xubuntu-desktop
```

---

### Post by bapoumba on 2007-07-03
> **Rocket2DMn said:**
> FYI: using the link bapoumba has provided for you gives you the Ubuntu alternate install cd (not Xubuntu), but once you everything loaded, installing "xubuntu-desktop" and setting that as your default login session will basically have you using xubuntu (the Xfce environment rather than Gnome).
```
sudo apt-get install xubuntu-desktop
```
Sorry, yes. And thanks Rocket2DMn :)

To get the alternate CD, tick the box below "download".

I could not use the live CD to install on my old laptop.

---


---
title: "format"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by alanc on 2007-08-13
:) Hi.    Can someone please tell me how i go about formmating the hard drive that i have
         Ubuntu on. I want to instal Ubuntu on to another hard drive, so my daughter can use this
         hard drive for all of her songs & photos. I know how to format in Windows XP ,but
       windows will not recognise the hard drive with Ubuntu on, so i cannot find it in Windows.
      Hope you can understand all of that.
                                                                            Regards alanc

---

### Post by Dark Seraphim on 2007-08-13
oh um hmmm complicated have you got a spare cd if you download partedmagic and burn it to a disc, you have like a live cd for formatting, its about 40 mb I think. also it has to be fat or ntfs for windows to see it.

---

### Post by Tyke91 on 2007-08-13
Download the Gparted live cd (gnome partition editor) and just format it that way (you can also use your ubuntu live cd as this comes with gparted on it)

---

### Post by jw5801 on 2007-08-13
The GParted LiveCD is the better option, Ubuntu keeps trying to mount the partitions you're trying to edit which messes things up, plus it's a much newer version of GParted with a few more options (like moving an ext3 partition).
It can be found [here.](http://gparted.sourceforge.net/livecd.php)

---

### Post by alanc on 2007-08-14
:)  Hi     I installed Gpart, as you suggested, but when i found it, it said,  There is no installed
        viewer capable of displaying the document.  So i don,t know where im at, hope you can
       help me some more, i,m a real beginner at this O S but i would like to get to understand
       it a lot better.
                                                        Regards     alanc

---

### Post by ramjet_1953 on 2007-08-14
Generally, gparted is not of much use, if you are running it on a drive that is mounted.

As was stated earlier, it is MUCH better to download the gparted LIveCD and then burn the iso image to CD and then boot from the CD.

You can get the gparted LiveCD from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Regards,
Roger :cool:

---

### Post by alanc on 2007-08-16
:) Hi.   That is what i had, gpart Livecd, and that is what came up when i
         found it. I wouldn,t know how to burn it to a cd or dvd even if it
         had came up as being installed.
                                                  Regards    alanc

---

### Post by jw5801 on 2007-08-17
The file you downloaded is an .iso, an image of a CD (exactly the same as the Ubuntu CD when you downloaded that). You'll need to burn the CD to disc, open up Brasero (Applications > Sound & Video > Brasero Disc Burning Application) and click on "Burn image" then put in a blank CD, click on the 'path' part and find the iso you downloaded and then click burn (tell it to use a reasonably slow speed, like 4x). Then restart you computer and boot using the CD (just like you did when you installed Ubuntu). You'll now be able to run GParted outside of Ubuntu to reformat the disc!

---

### Post by alanc on 2007-08-17
:) Hi.  There is no Brasero in my Sound & Video, i have - Movie player- Rhythmbox music player
           - Serpintine audio cd creator- Sound juicer cd extractor-Sound recorder.  I have searched         
          for Brasero, but it couldn,t find it. Thank-you for your help, i,ll keep searching around
        until i see if you will help me again.
                                                                            Regards     alanc

---

### Post by jw5801 on 2007-08-18
```
sudo apt-get install brasero
```

---

### Post by julian67 on 2007-08-18
Actually Brasero is not needed, you can just right click on the .iso file and choose the option "write to disc". You need a blank CD in the drive, everything else is automatic.

---

### Post by alanc on 2007-08-23
:) Hi.   I found K3B and that did it for me. The only thing is, i couldn,t
        open my pc at all in any OS.  So i installed Ubuntu again, with of course Win:xp and same thing happened again, i have done that 3 times
    and same thing every time, i cannot even find the external hard drive i have to format it again, i do not know how i go about that.
                                            Regards    alanc

---

### Post by Aishiko on 2007-08-23
Also Source Forge has a ext3 filesystem patch or driver for Windows.  You can try that as well.

---

### Post by bodhi.zazen on 2007-08-23
If you have installed Ubuntu to a new partition you can format the old in several ways.

There are two steps, making the partitions (fdisk) and formatting the partitions.

First, and easiest, is to install gparted :

```
sudo apt-get install gparted
```

The run gparted as root :```
gksu gparted
```

there is a pull down menu on gparted to select various hard drives.

OR you can partition from the command line.

The CLI tools are fdisk and mkfs

[http://linux.omnipotent.net/article.php?article_id=6979](http://linux.omnipotent.net/article.php?article_id=6979)

This link has information on formatting.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Look near the bottom of the first post on that second thread :)

---

### Post by bigboy_pdb on 2007-08-23
I would recommend buying the new hard drive, installing it, and installing Ubuntu on it first. Then you should boot from it and reformat the other hard drive. Otherwise, you can just use a Live CD to reformat it.

You can reformat it using "fdisk". I wrote another response that explains how to do it:
[http://ubuntuforums.org/showthread.php?t=482618#postmenu_2901984](http://ubuntuforums.org/showthread.php?t=482618#postmenu_2901984)

I've never used GParted, but I'm pretty certain that it would be easier than using "fdisk".

---

### Post by Aishiko on 2007-08-23
I've found that my community college (CC) Computer Department is quite willing to give away LiveCDs of Linux and help you download and burn your own.  Heck my Lunix class teacher is having us us Red Hat but his computer is running Ubuntu.  Red hat is being used only because it has software to make the grading process eaiser, otherwise he said he won't really care what Linux flavor that the students used for the class. 

So if you don't have a LiveCD or a way to make one go and talk to Computer Teacher at your local CC or Uni that teaches Lunix.  I'm pretty sure they'd bewilling to help.

---

### Post by alanc on 2007-08-24
:)  Hi.    Thank-you for all your help, i have succeeded in formatting my
      ex hdd, so thats OK, BUT I,M NOT SURE ABOUT UBUNTU
     I might have to buy another hdd, and see how that goes, i have lost
     that much time installing & uninstalling, it,s unbeleivable.
                                         Regards   alanc

---

### Post by bigboy_pdb on 2007-08-25
> **alanc said:**
> 
... i have succeeded in formatting my ex hdd, so thats OK, BUT I,M NOT SURE ABOUT UBUNTU
     I might have to buy another hdd, and see how that goes, i have lost
     that much time installing & uninstalling, it,s unbeleivable


If by "ex hdd" you mean external hard drive then that might be part of the reason why you're having problems installing Ubuntu. It is possible to do it on an external hard drive by using the normal installation method and making changes to some of the files (and possibly the **[EDIT]**BIOS**[/EDIT]**) in order to have your computer boot from it. I think that it's easier and better (since your hard drive will get pretty hot if the OS is constantly writing to the drive) to either get a new internal hard drive (but make certain that the cables and the jumpers are set up properly) and install Linux on it or to use GParted to resize your Windows partition, add a new partition, and install Linux on the new partition (but make certain that you defrag Windows first).

**[EDIT]**
I initially wrote registry in the above statement and it should have read BIOS. Your Windows registry is in no way affected by installing Linux to an external hard drive. Thank you jw5801 for pointing out that error (in the following post).
**[/EDIT]**

---

### Post by jw5801 on 2007-08-25
Why would you need to change anything in "the registry" in order to make your computer boot from it? Booting from an external drive is exactly the same as booting from a CD or a USB flash drive... or a second internal drive! All of which is handled by the bios, usually, so you shouldn't have to change anything in the Windows partition to do it.
You're right about it getting hot though, but if it's properly housed then it should be fine.

---

### Post by bigboy_pdb on 2007-08-25
> **jw5801 said:**
> Why would you need to change anything in "the registry" in order to make your computer boot from it? Booting from an external drive is exactly the same as booting from a CD or a USB flash drive... or a second internal drive! All of which is handled by the bios, usually, so you shouldn't have to change anything in the Windows partition to do it.
You're right about it getting hot though, but if it's properly housed then it should be fine.

When I first read your post I was thinking, "What are you talking about? I didn't say anything about the registry". Then I reread my post and there it was:

> **bigboy_pdb said:**
> It is possible to do it on an external hard drive by using the normal installation method and making changes to some of the files (and possibly the registry) in order to have your computer boot from it.

I meant to say BIOS. That's what I was thinking when I wrote it and I have no clue why I wrote registry (it was right before I went to bed and I was starting to fall asleep so I must have been tired). Sorry about that typo.

---

### Post by jw5801 on 2007-08-25
Haha. The joys of posting whilst half asleep!

---

### Post by ellgor on 2007-08-26
Hi,

Have had much the same trouble as you and have come across Disk-Manager ( I'm on Dapper-6.04, fully updated, and using Gnome) which is in preferences (drop down list)
when you open the disk-manager a list (pictures as well) of all drives etc is shown on the left with options over on the right.
Like you I had tried all suggestions, rename this insert that, and still couldn't access the drive, anyway if you have the disk-manager opened then click on the drive you want to adjust, over on the right click on partitons, thats under Storage Properties, and more options will be made available, ie FORMAT or change access etc.
I havent tried out the formatting part yet so if you do and it works let us know.

Regards, Ellgor.

---


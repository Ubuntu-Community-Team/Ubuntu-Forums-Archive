---
title: "Many failed attempts to install"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by gullwingdoors on 2007-02-15
I am trying to install Ubuntu on a computer with no success so far.

I have mainly been trying the live/install CD for Ubuntu, but I keep getting this:

```
Uncompressing Linux... Ok, booting the  kernel.
[  330.882780] Buffer I/O error on device hdc, logical block 178793
[  332.697344] Buffer I/O error on device hdc, logical block 178793
[  334.521938] Buffer I/O error on device hdc, logical block 178793
[  336.346460] Buffer I/O error on device hdc, logical block 178793
[  338.170875] Buffer I/O error on device hdc, logical block 178793
[  339.995428] Buffer I/O error on device hdc, logical block 178793
```

It sits there like that for a long time, then spits out another six lines like the ones above but with different numbers in the brackets.

I thought it might be a poorly burned cd, so I re-burned the iso onto another cd of a different brand and it did the same thing.

Any ideas?

---

### Post by dbbolton on 2007-02-15
sounds like your hard drive is bad.

do you know how to run a hard drive test in BIOS ?

---

### Post by gullwingdoors on 2007-02-15
No, how do you do that?

---

### Post by dbbolton on 2007-02-15
you have to hit either F10 or F12 as soon as your computer turns on, when the manufacturer's splash comes up. for instance, mine says "Compaq" and at the bottom "press F10 to enter setup." this screen is only up for a second though.

then, the BIOS menu will come up. with mine (PhoenixBIOS Setup Utility), there is a menu at the top with Main, SEcurity, Advanced, Tools, Exit. you navigate with the arrow key over to Tools, and then down to Hard Drive Self Test and press enter.

---

### Post by gullwingdoors on 2007-02-15
I know how to get to the BIOS (Fn/ F1 for my computer), but I don't see any sort of hard drive test listed there.

It is a Dell Latitude Notebook. Maybe this particular model doesn't have a hard drive test built in?

---

### Post by moffa on 2007-02-15
Are you installing it to a newly formatted hard drive or are you dual booting?  If you're dual booting, I suggest loading up Windows and running a full hard drive scan, it'll take a long time to do.  Make sure all the sectors are checked, even the free ones.

I had that same problem with an older version of Ubuntu and used the alternate install cd to make it work.

---

### Post by chrish670 on 2007-02-15
Dell drives usually contain 3 partitions.  1 is for Windows, 1 is where the Factory Disk Image for Recovery is burned, and the last (8mb and usually accessible from Boot menu) is the Service and System testing partition.  I don't exactly know what they call it. If you have DELL Disks.. assuming you recieved them with your laptop, there should be a bootable CD disc for conducting system tests.  If you didn't, and you wiped the harddrive...  All three partitions were removed.

---

### Post by gullwingdoors on 2007-02-15
I'm just overwriting everything that's already there. I tried the alternate cd as well, and it simply stops at one point and sits there forever.

---

### Post by chrish670 on 2007-02-15
Look up Mini.iso  in search.  Is what I used to install ubuntu desktop on my Toshiba Sattelite yesterday. Its just 8mb in size... make sure you have your internet connected to the laptop. High speed such as DSL is best.

---

### Post by gullwingdoors on 2007-02-15
> **chrish670 said:**
> Dell drives usually contain 3 partitions.  1 is for Windows, 1 is where the Factory Disk Image for Recovery is burned, and the last (8mb and usually accessible from Boot menu) is the Service and System testing partition.  I don't exactly know what they call it. If you have DELL Disks.. assuming you recieved them with your laptop, there should be a bootable CD disc for conducting system tests.  If you didn't, and you wiped the harddrive...  All three partitions were removed.

I don't have any discs for it. I just bought it (used obviously) for the purpose of messing around with Linux on it.

I have not formatted the drive, but I believe that the Linux install did get far enough to wipe the hard drive.

---

### Post by halitech on 2007-02-15
wouldn't hdc be the cdrom? I though hard drives showed as hda and hdb

---

### Post by gullwingdoors on 2007-02-15
I don't know anything about the code terminology, but I tried several different cd's with no success on any of them.

And, with the fact that this is a used laptop purchased for ten bucks, there's a good chance it may be the hard drive.

---

### Post by gullwingdoors on 2007-02-15
> **chrish670 said:**
> Look up Mini.iso  in search.  Is what I used to install ubuntu desktop on my Toshiba Sattelite yesterday. Its just 8mb in size... make sure you have your internet connected to the laptop. High speed such as DSL is best.

I will give that a try, but I am on a college campus which requires me to log onto their system with username and password to gain access to the internet through their proxy, so I'm not sure if it will be able to connect well just through the default installation.

---

### Post by chrish670 on 2007-02-15
[http://www.ubuntuforums.org/showthread.php?t=360291](http://www.ubuntuforums.org/showthread.php?t=360291)  << this is where the mini.ISO is located at.  I just had to search for it.  Wanna thank the bloke who recommended it..

---

### Post by 3rdalbum on 2007-02-15
/dev/hdc is the CD-ROM drive. It looks like the disc has been burnt at too fast a speed, or that the ISO was corrupted as you downloaded it, or that your CD-ROM drive is failing.

---

### Post by gullwingdoors on 2007-02-16
Hmm, in that case, it's probably the cd drive, because the internet connection here is great, and I burned it at the lowest speed.

Is there anyway to load the files on to, and boot from a flash drive?

---

### Post by dbbolton on 2007-02-16
you can boot damn small from a usb drive. it's also debian based

[http://damnsmalllinux.org/wiki/index.php/USB_Booting](http://damnsmalllinux.org/wiki/index.php/USB_Booting)

---

### Post by gullwingdoors on 2007-02-16
I trying the mini cd right now, but I'm not sure I'm doing the proxy info correctly.

Here is what I'm trying:

[http://cmckn953:mypassword@dormproxy.bju.edu:8080/](http://cmckn953:mypassword@dormproxy.bju.edu:8080/)


Obviously my password is changed, but otherwise does that look like the correct format it should be in?

---

### Post by IronMac on 2007-02-16
I had similar error messages and problems when I was doing the install from a DVD. In the end, I went with the CD version that was included in the "Beginning Ubuntu Linux" book.

---


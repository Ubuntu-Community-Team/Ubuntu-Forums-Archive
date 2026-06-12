---
title: "Won't boot after installing"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by secretblue3 on 2007-05-30
I'm trying to install Ubuntu 7.04 as a dual-boot with Windows XP.  It looked great on the Live CD and installed without a problem, until I removed the Live CD and rebooted.  The GRUB menu came up, and I selected the first Ubuntu choice.  All I got was a black screen with a blinking cursor.  I let it sit for 10 minutes and nothing happened.  I'm not able to input anything, and it doesn't respond to Ctrl-Alt-Backspace or Ctrl-Alt-Fkeys.  I also can't boot into Recovery Mode; it does the same thing.

I thought it might be hardware, even though everything worked on the Live CD, so I tried the suggestion here: [http://ubuntuforums.org/showthread.php?t=417421&highlight=blinking+cursor+first+boot+after+install]("http://ubuntuforums.org/showthread.php?t=417421&highlight=blinking+cursor+first+boot+after+install") to compare the /etc/X11/xorg.conf with the Live CD version, but they are the same.

I can edit files through Windows with fs-driver.  Does anyone have any suggestions for me?  I would really appreciate it.

I've looked around and all the similar posts were unresolved and involved earlier versions.

This is my system:
Dell Optiplex 320 Pentium D
128MB ATI Radeon X1300 (is this the problem?)
Dell 2007WFP monitor
160GB SATA hdd (dual-booting XP)

Thanks for your help.

Edited to add:  I first tried installing with a Xubuntu Live CD, and I checked both of them for errors before installing.

---

### Post by secretblue3 on 2007-05-31
*bump*

Sorry, but I'm hoping someone will see my question this morning.

---

### Post by bernied on 2007-05-31
I'm not sure how much this will help, but since you've been waiting so long for a reply...

See if you can find the file /var/log/dmesg. If you can find it, post it here.
This is a log of kernel startup messages.

There are other log files in the same directory - might be worth a look for anything that says error or kernel panic or other scary stuff.

The ATI graphics card may be part of the problem, but I don't think that should stop you booting into recovery mode (though I'm not sure on this, as I don't run 7.04).

---

### Post by bernied on 2007-05-31
This one is a bit of a long shot (again I'm not sure if things have changed a lot with 7.04) so read any other replies and use your own judgement before trying this (you could at least have a look at the file and tell us what you see). I'm guessing that the problem occurs before any graphical stuff starts up ...

The next place to look is in /etc/X11/xorg.conf
This is the main configuration file for the X (graphical) windows system.

In this file, you should find something like this
```
Section "Device"
        Identifier      "...something about your ATI card..."
        Driver          "...the driver, maybe ati or radeon..."
        ...some more lines...
EndSection
```
This defines the driver used for your graphics card and its settings.

You will also find a section like this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "...the same description as in the Identifier field of the Device section..."
        Monitor         "...some description of your monitor..."
        ...and more...

```
If you are feeling very adventurous (and you can't find anything in the log files), you could try the following:
- make a backup copy of the file /etc/X11/xorg.conf (don't continue if you can't do this)
- open /etc/X11/xorg.conf for editing and add a new Device section, just below the previous one, like this:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
EndSection
```
- in the Screen section, comment out the line for Device, and add a new one, like this:
```
Section "Screen"
        Identifier      "Default Screen"
        # Device          "...the same description as in the Device section..."
        Device "Generic Video Card"
``` - see if it boots now

So, what you've done is to tell the X server to use a generic driver for your video card, instead of the one previously specified. If it works this will give a much lower resolution than you are used to and generally look terrible, but it will give you access to your desktop environment.

[EDIT] If you want to revert to your original setup, you can just comment out your new line in the 'Screen' section, or you can replace the file with its backup.

---

### Post by secretblue3 on 2007-05-31
Thank you very much for your replies.  I will try your suggestions when I get off work.

(Sorry if I sounded impatient that no one had replied.  I just didn't want my post to be completely buried.)

---

### Post by secretblue3 on 2007-05-31
> **bernied said:**
> 
See if you can find the file /var/log/dmesg. If you can find it, post it here.
This is a log of kernel startup messages.

There are other log files in the same directory - might be worth a look for anything that says error or kernel panic or other scary stuff.

This is all /var/log/dmesg says:
(Nothing has been logged yet.)

Most of the other logs are empty as well.  

The only one that seems to have errors is /var/log/bootstrap.
This is the first part of it (apparent problems in bold, but it might be normal for all I know):

> [B]dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.[/B]
Setting up base-files (4ubuntu2) ...

dpkg: regarding .../dpkg_1.13.24ubuntu6_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libc6 (>= 2.5-0ubuntu1)
**dpkg: warning - ignoring pre-dependency problem !**
dpkg: regarding .../dpkg_1.13.24ubuntu6_i386.deb containing dpkg, **pre-dependency problem**:
 dpkg pre-depends on coreutils (>= 5.93-1)
**dpkg: warning - ignoring pre-dependency problem !**
(Reading database ... 87 files and directories currently installed.)
Preparing to replace dpkg 1.13.24ubuntu6 (using .../dpkg_1.13.24ubuntu6_i386.deb) ...
Unpacking replacement dpkg ...
**dpkg: dpkg: dependency problems, but configuring anyway as you request:**
 dpkg depends on libc6 (>= 2.5-0ubuntu1); however:
  Package libc6 is not installed.
 dpkg depends on coreutils (>= 5.93-1); however:
  Package coreutils is not installed.
Setting up dpkg (1.13.24ubuntu6) ...

I don't know what the "configuring anyway as you request" means.  The only error I had during installation was:
"Warning.  Filesystem doesn't have expected sizes for Windows to like it.  Cluster size is 2k(1k expected): number of clusters is 28034 (55960 expected); size of FATs is 110 sectors (219 expected)."  

The only FAT partition is the Dell FAT16 recovery partition, which I wouldn't think would affect the Ubuntu installation at all.  I didn't ask the partitioner to do anything to it.

Thanks for any insight anyone can give me.

---

### Post by secretblue3 on 2007-05-31
> **bernied said:**
> The next place to look is in /etc/X11/xorg.conf
This is the main configuration file for the X (graphical) windows system.

In this file, you should find something like this
```
Section "Device"
        Identifier      "...something about your ATI card..."
        Driver          "...the driver, maybe ati or radeon..."
        ...some more lines...
EndSection
```
This defines the driver used for your graphics card and its settings.

You will also find a section like this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "...the same description as in the Identifier field of the Device section..."
        Monitor         "...some description of your monitor..."
        ...and more...

```
If you are feeling very adventurous (and you can't find anything in the log files), you could try the following:
- make a backup copy of the file /etc/X11/xorg.conf (don't continue if you can't do this)
- open /etc/X11/xorg.conf for editing and add a new Device section, just below the previous one, like this:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
EndSection
```
- in the Screen section, comment out the line for Device, and add a new one, like this:
```
Section "Screen"
        Identifier      "Default Screen"
        # Device          "...the same description as in the Device section..."
        Device "Generic Video Card"
``` - see if it boots now


The xorg.conf file already said "Generic Video Card" and "vesa", so nothing to change.

Anything else I can try?  :)

---

### Post by secretblue3 on 2007-06-02
In case anyone has a similar problem and is reading this, I tried a lot of other things and never got a regular installation to work.  However, it now appears I have a working wubi installation.

---


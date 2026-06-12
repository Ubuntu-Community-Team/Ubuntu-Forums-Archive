---
title: "several questions on install powerbook g4 ppc"
date: 2006-06-27
forum: Apple PPC Users
---

### Post by Digitallysick on 2006-06-27
Ok i have ubuntu 6.06 and want to install on my powerbook g4, with about a 8gb partition. When i put the disk in and hold down C, boot up into Live mode, the trackpad on my laptop moves sooooo slow and how do i partition my HD? the wiki said something about resizing my current partition or "shinking it" ??  i dont get how i am supposed to partition? manual? and once i do that, and install how do i fix the track pad to move just like it does on osx

---

### Post by zachws on 2006-06-27
hey i had the same problem with my ibook g4. ignore the slow mouse speed for now, it's a fact of life.

have you already created a partition for ubuntu? if not you need to go to the terminal by going to accesories in the menu in the top left corner.
in terminal, type 'sudo parted' to get to the partitioner, then type 'print' in parted to see your partitions. type 'resize' to resize your main one into multiples.

if you already have partitioned run in the installer (note: choose largest free space, not manual partitioning within the installer otherwise the bootstrap partition won't be created)

finally, once you have a hot new ubuntu installation, where your mouse problem will still exist, go again to your terminal, type: 
"sudo gedit /etc/X11/xorg.conf"

and put in the following in the section that corresponds (it will say synaptec or something similar)

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "20"
        Option          "MinSpeed"              "0.3"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.015"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
EndSection
```

This is all in the forum but I will post links if you need them.

---

### Post by zachws on 2006-06-27
Here is the thread for resizing the partition:

[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

---

### Post by N8K99 on 2006-06-27
Here's the basic outline.

* backup data someplace else
* reinstall OS X
** during this installation use Disk Utility to repartition HD, this will erase the drive which is why you backup everything
** create HFS+ for OS X and Free Space for ubuntu
* install OS X
* Install ubuntu into Largest continuous free space
* then copy data into OS X

boot up, select linux when prompted and enjoy!

---

### Post by Digitallysick on 2006-06-27
errrr i dont want to reinstall osx, and i dont have much way to backup 80 gigs of data...... is that the only option?

---

### Post by 3rdalbum on 2006-06-28
[QUOTE=Digitallysick]errrr i dont want to reinstall osx, and i dont have much way to backup 80 gigs of data...... is that the only option?[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=89960]("http://ubuntuforums.org/showthread.php?t=89960")

That's the other option, but the method is quite new (comparatively) and it *could* possibly damage your OS X partition (so try and do a backup first). But then, running fsck on a mounted partition supposedly causes damage, and I've done that before with no ill effects.

---

### Post by zachws on 2006-06-28
that (resize) method worked fine for me. just remember to turn of journaling. the tutorial will explain it all.

---


---
title: "Accessing hard disc files"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Don Cox on 2007-04-06
Using the 6.10 livecd what is the procedure for accessing files on the hard disc in the Windows (XP) partition? I should like to test My Music files with Amarok which is easy to install via Add/Remove.

Don Cox

---

### Post by indytim on 2007-04-06
Don,

I assume you did not hit the link at the top of the forum "mount".  Had you done so, you would have found the following detailing exactly what you are looking for.

[http://ubuntuforums.org/showthread.php?t=402054]("http://ubuntuforums.org/showthread.php?t=402054")

IndyTim

---

### Post by Stew2 on 2007-04-06
> **indytim said:**
> Don,

I assume you did not hit the link at the top of the forum "mount".  Had you done so, you would have found the following detailing exactly what you are looking for.

[http://ubuntuforums.org/showthread.php?t=402054]("http://ubuntuforums.org/showthread.php?t=402054")

IndyTim

Good info. I didn't even know what that blue box with all the terms was. I had never moused over the terms before... I thought they were just key words for a search engine. :D

---

### Post by Don Cox on 2007-04-06
> **indytim said:**
> Don,

I assume you did not hit the link at the top of the forum "mount".  Had you done so, you would have found the following detailing exactly what you are looking for.

[http://ubuntuforums.org/showthread.php?t=402054]("http://ubuntuforums.org/showthread.php?t=402054")

IndyTim

I think you are presupposing a much greater knowledge than I possess as a first time poster. 
Copying the three lines of code into the terminal and hitting enter did not produce a satisfactory outcome, and I wonder if anyone would be kind enough to volunteer to guide me through the required steps.

Don Cox

---

### Post by Don Cox on 2007-04-07
IndyTim

I spent a lot of time researching this issue before posting to the forum.

Not only was your advice useless, it was expressed in such an authorative and dismissive manner that anybody reading it might consider further comment or advice quite superfluous.

I regard this as a disagreeable welcome to Ubuntu, and while comparisons are invidious the same procedure can be accomplished graphically with one click using a PCLinuxOS livecd.

Don Cox

---

### Post by freebird54 on 2007-04-07
I guess you got a bit unlucky there.  Some of that would apply  - but it was aimed at a user who has been at it a while.  Here's what I would do.

Open a Applications->Accessories->Terminal

Enter this line into the terminal to determine what the drive is called, and what filesystem it uses:

```
sudo fdisk -l
```

This will give you output similar to this

```
 Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3824    30716248+   b  W95 FAT32
/dev/hde2            4869        5129     2096482+  82  Linux swap / Solaris
/dev/hde3            5130       19457   115089660   83  Linux
/dev/hde4            3825        4868     8385930   83  Linux

Partition table entries are not in disk order

```

If you can post this code  (keyboard copy is <ctrl><shift><c>, then <ctrl><v> into the message editor - then highlight the text and hit # in the menu bar above) - then I can give you a command line that will do the job.

OR - here are the two most probable solutions:
1 (if FAT32)
```
sudo mkdir /mnt/ubuntu
sudo mount -t vfat /dev/hda1 /mnt/ubuntu
```

or 2 (if NTFS)

```
sudo mkdir /mnt/ubuntu
sudo mount -t ntfs /dev/hda1 /mnt/ubuntu
```


BTW - the graphical way is coming to Ubuntu on the 19th I believe, with the Feisty Fawn (7.04) release due at that time... and even now, if you install it will pick up the drive automatically and mount it for you.

---

### Post by Don Cox on 2007-04-07
freebird54

Thank you so much for all your help.

I cheated and successfully used the 7.04 beta disc which was  already to hand ... and look forward to the 19th. In the interim I shall look at and learn from your instructions.

The issue is resolved and I will try to edit the OP accordingly. 

Don Cox

---

### Post by Don Cox on 2007-04-07
Hi freebird54

I hope I have done this properly for you. BTW what is correct way to notify that an issue is resolved?

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7062    56725483+   7  HPFS/NTFS
/dev/sda2            7063       12161    40957717+   5  Extended
/dev/sda5            7063       11970    39423478+  83  Linux
/dev/sda6           11971       12161     1534176   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Don Cox

---

### Post by Duck2006 on 2007-04-07
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

This may help

---

### Post by freebird54 on 2007-04-07
TO mark an issue as "RESOLVED', you Edit the original message.  (a box on the bottom right gives you that option).  Once you are in the editor, at the bottom right a choice for Go Advanced is available.  When you select that, there is a 'radio button' choice for Resolved or Not Resolved.  Save to lock in your choice.

BTW - The 2nd option should work from the live CD - using NTFS as the 'filesystem' entry.  As already mentioned, all recent versions of the os should automatically detect and mount that drive for you when installing (usually as media/windows/ ).  That makes it:

```
sudo mkdir /mnt/ubuntu
sudo mount -t **ntfs** /dev/**sda1** /mnt/ubuntu

```

and more information can be found by

```
man mount
```

as for most commands. (as well as any number of Howtos some of which you have been directed to)

Again - sorry about your first answer!  It can be difficult to clearly show 'intent' on a text only medium...

---

### Post by Don Cox on 2007-04-08
I'm grateful to all three of you and now know a great deal more than I did before posting. Could not agree more about 'intent' and the medium.

Don

---


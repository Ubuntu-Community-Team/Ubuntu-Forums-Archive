---
title: "a second HDD"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2007-01-18
I have an extra HDD I want to put in my ubuntu server but i know when you put a second HDD in a windows machine you have to follow a bunch of step. but what I am asking is how would I go about this?

---

### Post by JamieC on 2007-01-18
Have you connected it and is it detected by the BIOS?

If so can you post the output of the following please:
```

sudo fdisk -l

```

---

### Post by RED WIND on 2007-01-19
now wut I get is this

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris
```

Now wut???

---

### Post by taurus on 2007-01-19
Did you connect your second harddrive (set the jumper on the back to slave) to your machine because it shows you only have one harddrive right now?

---

### Post by halitech on 2007-01-19
do you not have an hdd showing? if not, the computer is not seeing the drive in the BIOS

---

### Post by irish_flu on 2007-01-19
Start your computer up into the "BIOS", usually accessed right at the start of boot-time.  There will be text on your screen that says something like "Press DEL to enter setup".

Go in there, and you'll see the area where your hard drives and CD/DVD drives are listed.  See if the new drive is there.  Assuming you know how you hooked it up (say on IDE1 - Slave) navigate to the appropriate slot and choose "auto-detect".  Save your changes, then reboot and go back into your BIOS to make sure it's still there.

If the BIOS can't see it, no Operating System (Linux, Windows, nothing) will be able to.

---

### Post by RED WIND on 2007-01-19
my BIOS is not detecting it

---

### Post by taurus on 2007-01-19
Did you check the jumper on the back of the drive to make sure you have set it properly?  The first harddrive in your machine should be set as master and it should connect to the end of the cable ribbon.  The second should set to slave and should connect to the middle connector of the same ribbon.  Then, the other end goes into your mobo.

---

### Post by RED WIND on 2007-01-19
yeah I tried a bunch of positions but none of them work

---

### Post by taurus on 2007-01-19
If the BIOS doesn't see your second harddrive, Ubuntu can't see it either.

---

### Post by RED WIND on 2007-01-19
any suggestions on wut I should do

---

### Post by taurus on 2007-01-19
How old is your machine (spec) and what is the capacity of the second harddrive?  Do you have another computer that you can connect it to to see if it would read that harddrive at all?

---

### Post by RED WIND on 2007-01-19
the computer is a couple years old, I cant tell you much more b/c it was given to me and its 200GB and it work I just switched it out of my main machine

---

### Post by Warpd on 2007-01-19
If you have an 80-pin cable for connecting your HDD, you may have to set both drives to CS (cable select).  Also, some drives don't play well with others.  I have some issues when mixing drives from different manufacturers.  

As a start, try plugging in only the second drive you want to add, in the primary or secondary position, and see if BIOS can find it.

---


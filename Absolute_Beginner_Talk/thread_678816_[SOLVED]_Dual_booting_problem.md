---
title: "[SOLVED] Dual booting problem"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Dalston on 2008-01-26
Hi Could someone help me out,  I have 7.10 as my main operating system but I needed to have xp for my sony psp.  So I installed xp last night and I knew that ubuntu wouldnt show up at boot by default  so  I used the grub boot disk, but I can only work out how to have ubuntu as the only operating system showing up or i have to use the disk to boot xp.   Could someone tell me what im doing wrong?   thanks in advance

---

### Post by mikeyphi on 2008-01-26
Try this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?)

---

### Post by Dalston on 2008-01-26
MY problem now is that Ubuntu shows up at boot but xp doesnt.

---

### Post by mikeyphi on 2008-01-26
> **Dalston said:**
> MY problem now is that Ubuntu shows up at boot but xp doesnt.

Look at item 6 from the guide I posted!!
Hope it works for you!

---

### Post by jw5801 on 2008-01-26
You'll need to edit /boot/grub/menu.lst to tell grub that it can boot Windows. You'll need to know which drive and which partition your Windows install is on and get it in a format similar to (hdx,y), where x is the drive and y is the partition starting at 0 and counting up (ie. 0 is the first drive, 1 is the second etc, /dev/sda1 would correspond to (hd0,0)). So open menu.lst for writing:
```
gksu gedit /boot/grub/menu.lst
```
Then add right at the very bottom an entry that looks like the following:
```
title           Windows XP Home Edition
root            (hd0,1)
makeactive
chainloader     +1
```
But you'll need to replace the (hd0,1) with whereever your Windows install is located. If you're not sure which partition you should use, run ```
sudo fdisk -l
```and post the output here and we should be able to give you a fair idea which is your Windows partition.

---

### Post by jan quark on 2008-01-26
perhaps this guide will help you 
I stumbled across 

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

just select what configuration you want

---

### Post by Dalston on 2008-01-26
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9b18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b327b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       25016   200940988+  83  Linux
/dev/hda2           25017       30213    41744902+   7  HPFS/NTFS
/dev/hda3           30214       30401     1510110    5  Extended
/dev/hda5           30214       30401     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x898170f3

   Device Boot      Start         End      Blocks   Id  System

XP is on the 40gig  partition

---

### Post by Dalston on 2008-01-26
so i presume i add

title           Windows XP
root            (hda,2)    
makeactive
chainloader     +1

is that right?

---

### Post by mikeyphi on 2008-01-26
> **Dalston said:**
> so i presume i add

title           Windows XP
root            (hda2)
makeactive
chainloader     +1

is that right?

NOT quite!!

Post the file    /boot/grub/menu.lst

at least the section dealing with your windows.

---

### Post by jw5801 on 2008-01-26
> **Dalston said:**
> so i presume i add

title           Windows XP
root            (hda,2)    
makeactive
chainloader     +1

is that right?

Close, remember that we start counting from 0, it'll probably be:
```
title           Windows XP
root            (hd1,1)    
makeactive
chainloader     +1
```

"sda" and "hda" are simply different types of drives, since /dev/sda is listed first I would assume it is the first drive (hd0) and /dev/hda is listed second (hd1). Since your windows partition is the second on this drive it gets the label (hd1,1).

You'll have to hit Esc sometime during bootup to see the menu where you can choose which OS you'd like to boot to. You can change the settings for automatically displaying the menu, and adjust how long it shows for earlier on in the file. After you're done, you might also need to run the following to make it take affect, I'm not sure though:
```
sudo update-grub
```

This is the section that determines whether to display the menu during boot or not:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         6

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
You'll notice I've commented out the "hiddenmenu" line (the # at the start of the line denotes a comment, a line that is ignored on processing), which means the menu will display. The first section tells it to display for 6 seconds before booting the default OS.

---

### Post by Dalston on 2008-01-26
Thanks for your help i've sorted it now,  it was 

title           Windows XP
root            (hd0,1)    
makeactive
chainloader     +1

Xp was on the first hard drive second partion.   I didnt know about starting to count from 0 it makes sense now.  thanks for your help,  this forum never fails to solve my problems.

---

### Post by alex_anthony on 2008-01-26
can I ask what you needed for your PSP on windows? mine works fine with linux.

---

### Post by Dalston on 2008-01-26
Just for accessing the memory stick,  I couldnt do it for some reason.  Did you do anything to make it show up on yours?

---

### Post by Dalston on 2008-01-26
I dont know why but my psp shows up now.  Have not got a clue why it didnt show up before.   I must of changed a setting on my psp slim I only got it yesterday.

---


---
title: "Getting rid of GRUB"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Namtsae on 2007-02-25
Yes, I have read the other threads. I need to run fixmbr in the dos prompt in order to get rid of it. However I cannot get into the prompt because Grub won't let me boot into Windows (error 17). I'm currently using a live CD, Is there a way to fix error 17, because I haven't found i. Nor have I found a way to berid of Grub in Ubuntu. To break it down:

1. Getting into DOS prompt through bootup
2. Fixing Error 17
3. Stop Grub in Ubuntu live CD.

Any will fix the problem.
Thank you.

---

### Post by yabbadabbadont on 2007-02-25
Boot your Windows installation cd.  Then take the option to boot the recovery console.  Then you should be able to run fixmbr and fixboot if needed.

---

### Post by Namtsae on 2007-02-25
My computer is a gateway. The disk that ships with it doesn't allow me into the recovery console. It boots to CD, then gives 2 options for formatting the hard drive. I've tried pressing R throughout the process, to no avail. I should have stated that before. Sorry.

---

### Post by Maestro23 on 2007-02-25
> **Namtsae said:**
> My computer is a gateway. The disk that ships with it doesn't allow me into the recovery console. It boots to CD, then gives 2 options for formatting the hard drive. I've tried pressing R throughout the process, to no avail. I should have stated that before. Sorry.

Might want to take a look at Super Grub disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by tlmarker on 2007-02-25
While trying to get a Ubuntu server working, I ran into the proble of error 17.  At first I thought "Oh s#%t, I lost Windows.

The way I got rid of the error 17 message was to do a complete install of Ubuntu from the live CD. It may seem like a lot of work, but it did let me get back to windows.

Hope it helps.
Regards,
Troy

---

### Post by yabbadabbadont on 2007-02-25
OK, now I understand the issue.  While you are booted on the live cd, open a terminal window and run "sudo fdisk -l".  Please post the output here.

---

### Post by Namtsae on 2007-02-25
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             532       12282    94389907+   7  HPFS/NTFS
/dev/hda2   *           1         531     4265226    b  W95 FAT32
/dev/hda3           12283       23900    93321585    7  HPFS/NTFS
/dev/hda4           23901       24321     3381682+   5  Extended
/dev/hda5           23901       24321     3381651   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by yabbadabbadont on 2007-02-25
OK, reboot the machine so that you get to the grub menu.  Once there, hit 'c' so that it puts you into the grub command line.  Then run the following commands:

rootnoverify (hd0,1)
makeactive
chainloader +1
boot

At that point is should try to boot you into windows.  If you get the same error as before, you might try tlmarker's suggestion.

---

### Post by Namtsae on 2007-02-25
> **yabbadabbadont said:**
> OK, reboot the machine so that you get to the grub menu.  Once there, hit 'c' so that it puts you into the grub command line.  Then run the following commands:

rootnoverify (hd0,1)
makeactive
chainloader +1
boot

At that point is should try to boot you into windows.  If you get the same error as before, you might try tlmarker's suggestion.

What do you mean GRUB menu? It doesn't make it to the menu in which I can select the OS. Stops right before that. All the other options didn't work. Haven't gotten super grub disk to work yet. I'll try that sometime soon.

---

### Post by yabbadabbadont on 2007-02-25
> **Namtsae said:**
> What do you mean GRUB menu? It doesn't make it to the menu in which I can select the OS. Stops right before that. All the other options didn't work. Haven't gotten super grub disk to work yet. I'll try that sometime soon.

Sorry, I misread your first post.  I thought that you were getting the grub error after you selected Windows from the grub menu...  Reinstalling like tlmarker suggested might be the easiest way to resolve things.

---

### Post by Namtsae on 2007-02-25
Tried that. Plenty of times. It locked up every time. Says it can't partition the space. And this was on an empty 89 gig partition. SGD didn't do a thing. I'm going nuts!

---

### Post by kittyhawk63 on 2007-02-25
Namtsae,
I had the same error 17 and then later an 18 error. I hope that you can find an easier solution than the one that I am going to offer you, but it works. It requires new installs.

If you have more than one HDD (hard drive) remove the one without Windows. Make the Windows HDD the Master unless it is already the Master.

Get a boot disk that will boot you onto the HDD. It will take you to the A: prompt.  

Find a disk that has fdisk on it. Run the fdisk command. (fdisk will get rid of GRUB.)

Using fdisk:
Start at number 4 and work yourself back up until number 1. Remove all partitions. When at number 1 create a new primary partition.

Insert Windows disk and turn off CPU. Turn it back on (boot up) and re-install Windows. 

I did not have to fdisk the Linux HDD. But I did do a new install after I had removed the Windows HDD. I connected only the Linux HDD and Linux defaulted to add GRUB to the Linux disk. Remember to make the Linux HDD the Master for re-installing Linux.

I reset the pins on the HDD and made Linux HDD my Master and Windows HDD my Slave.

I hope you find an easier solution.
KH

---

### Post by webofunni on 2007-02-26
I got grub error when i done some changes in partition using partition magic in windows. What ever changes that made to hd partitions after installing grub makes in error throwing one. Its better to go for a grub boot cd to override those errors while booting.

Also there are some windows based boot loaders for dual booting , I never tried them but i think they can handle those partition property changes

---

### Post by bigken on 2007-02-26
if dont have windows xp cd you can download the boot [floppies]("http://www.microsoft.com/downloads/details.aspx?FamilyID=55820edb-5039-4955-bcb7-4fed408ea73f&DisplayLang=en")

---

### Post by Namtsae on 2007-02-26
Well, I've tried SGD on a pendrive. Nope. Computer doesn't have a floppy drive. If I can just get into the DOS prompt, I'm sure I can handle it. Fixmbr. But nothing so far has worked. I can't reinstall. I have no floppy drive. I cannot get into the prompt at all...

Can anything be done? Or am I just not trying hard enough?

---

### Post by PsychoticSheep on 2007-02-26
I had the same problem a while back. pretty much as you described. Now i know this may sound stupid but a friend of mine suggested I try this  method (an it actually worked. It lets you into windows. Allowed me to back up my files etc and try and rewrite the mbr. I dont know if this will work for you but sounds like your at the stage where you'll try anything. Hopefully you have a floppy drive! [http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)

Good luck.

---

### Post by kittyhawk63 on 2007-02-26
> **PsychoticSheep said:**
> I had the same problem a while back. pretty much as you described. Now i know this may sound stupid but a friend of mine suggested I try this  method (an it actually worked. It lets you into windows. Allowed me to back up my files etc and try and rewrite the mbr. I dont know if this will work for you but sounds like your at the stage where you'll try anything. Hopefully you have a floppy drive! [http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)

Good luck.

I'll try this when push comes to shove. Thanks.

---

### Post by Patrick K on 2007-02-26
> **Namtsae said:**
> Well, I've tried SGD on a pendrive. Nope. Computer doesn't have a floppy drive. If I can just get into the DOS prompt, I'm sure I can handle it. Fixmbr. But nothing so far has worked. I can't reinstall. I have no floppy drive. I cannot get into the prompt at all...

Can anything be done? Or am I just not trying hard enough?

I'm a firm believer that all computer should have a floppy drive. If for nothing else than as a recovery medium. They are very cheap, under $10, and very easy to install. You might consider getting one. Of course, if the motherboard doesn't have a connection for one, which I think all do, then you may be out of luck.

---

### Post by kittyhawk63 on 2007-02-26
> **Patrick K said:**
> I'm a firm believer that all computer should have a floppy drive. If for nothing else than as a recovery medium. They are very cheap, under $10, and very easy to install. You might consider getting one. Of course, if the motherboard doesn't have a connection for one, which I think all do, then you may be out of luck.

I always have a 3.5 floppy drive just in case I need to take something to one of my friends with an older computer.

---

### Post by bigken on 2007-02-27
cant you borrow a copy of windows xp ?

---


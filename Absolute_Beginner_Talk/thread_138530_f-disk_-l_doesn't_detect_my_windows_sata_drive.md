---
title: "f-disk -l doesn't detect my windows sata drive"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by sony102600 on 2006-03-02
I'm trying to mount my windows drive(contains all my music ect), however, ubuntu doesn't seem to be able to detect it anyway, it is not listed when I do the f-disk command -l

Any ideas?

---

### Post by Sutekh on 2006-03-02
I don't get anything when I type ```
fdisk -l
```  Did you try ```
**sudo** fdisk -l
```
This might be stating the obvious to you, I just want to check the command that you used.

---

### Post by procras on 2006-03-02
1) make sure you run the fdisk command as root
2) Suppy a device address for fdisk such as 
/dev/hda for the first disk on the IDE interface
/dev/sda for the first disk on SCSI/SATA etc

3) Check to see what disk is used by your root partition with
$ mount | grep " / "
My system gives
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
        ^^^

This is the first partition on device sdb

Then if the windows disk is on a similar interface try
$ sudo fdisk -l /dev/sda

---

### Post by xmastree on 2006-03-02
Just to clarify the above. If you run fdisk with the **-l** switch, you don't need to supply a device address, it just lists what's there.

The result of **sudo fdisk -l** on mine gives this for my 80GB FAT32 sata disk:
```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   c  W95 FAT32 (LBA)
```
And in my fstab it's:
```
/dev/sda1       /mnt/sata       vfat    umask=000       0       0
```

---

### Post by Sutekh on 2006-03-02
Im so tired I forgot to post my fav guide for mounting Windows partitons

[http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

I still find this a good resource

---

### Post by sony102600 on 2006-03-02
Thanks guys..

Yeah, I did use sudo fdisk -l, sorry I didn't include that.  It does show the hard drive that linux is installed on, and its partitions.... but it shows nothing about the windows drive....

(This is day 3 of my linux experience... :-( , still no internet, still no windows drive recognition, still no mp3 playing, this has been rough)

anyway, thats for the help guys

---

### Post by xmastree on 2006-03-02
Very strange... It should show all drives, unless there's something weird in your BIOS. I'm not so familiar with sata drives, the one I have one is my first, and it just worked right away. :-k

Post the output of fdisk -l here, so we can take a look what is listed. Also, do you have a live CD? try booting from that, it may recognise it.

When you say 'windows disk', is the sata the one windows is installed on? Or just a data disk?

---

### Post by sony102600 on 2006-03-02
when I say windows disk, I mean that windows is installed on that disk.  I am running a two hard drive dual boot setup.

---

### Post by sony102600 on 2006-03-02
I am not sure how I will be able to get a copy of my fdisk -l results on this forum, I have been unable to get my internet connection up yet with ubuntu, and i do not have any floppy disk or removable media to save an output to..... the best I can say is the output is what you would expect if I didn't have that windows installed drive... it shows the drive linux is on and its partitions, and nothing else.

---

### Post by xmastree on 2006-03-02
hmm... So in the BIOS, the sata is the boot disk? How do you boot linux?
Mine is much different, I have a 40GB IDE (hda) split 20/20 with Windows and Linux, and my sata is just data so I always boot from the primary master.

---

### Post by sony102600 on 2006-03-02
In the bios... the sata drive is the primary boot option....so if I turn on the computer, it goes straight to windows..... however, if I want to go to ubuntu, I just press f11, which brings up the boot menu, and I can select my other harddrive to go to ubuntu.....

---

### Post by xmastree on 2006-03-02
Try setting the other hard drive as the primary boot in the BIOS. If that works, you could use the F11 trick to boot windows instead.

Although, I'm clutching at straws here, since I have a different setup...

---


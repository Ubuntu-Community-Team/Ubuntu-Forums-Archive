---
title: "Stuck with Grub error 18"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by steamshooter on 2007-05-24
This is an old box with a 1999 BIOS and a 160gb hard drive.
Trying to install 6.06 Dapper LTS and upgrade through the ranks to end up with Studio.

If I understand correctly from my research, my BIOS won't see the bootloader past a certain point and my bootloader *is* past this point on my hard drive. What I don't understand is how to move GRUB to a point where my BIOS will see it without destroying my XP partition. 

I've tried different BIOS settings and it changed from an 18 to a 17. I am now back to error 18. 

I do have an old 2gig hard drive not in use. Could GRUB be installed on it? Swap partition too?

I'm open to any and all suggestions. 
Thanks in advance
steamshooter

---

### Post by cox377 on 2007-05-24
You know i had exactly the same problem just 2 weeks ago with a 160gb hdd,

I didnt write it down but someone did talk me through it off the ubuntu IRC room,

If i remember correctly i had

100mb = /boot

10gb = /

150gb = /home


It was also recommended that I used LBA, i do hope this helps because i went round and round in circles trying to get this to work, once it worked it was fab.

CoXen

---

### Post by steamshooter on 2007-05-24
That sounds like what I'm trying to accomplish with the exception of an XP partition. I just can't figure out how to re-size my first partition (XP) without messing up XP.  

I have tried LBA, Auto and User settings in the BIOS. None of them seem to work for me.

I could have possibly avoided this if I did my research better before I installed.

Thanks cox377

---

### Post by ferpadro on 2007-05-24
You know, i have the same error. I remember having installed Hoary Hedgehog a couple of years ago, and then when i rebooted it it just freeze. I have an ASUS P4SP-MXSE Motherboard, 40 GB HDD, 512 MB RAM. I dont know what to do, i tested LBA, Match partition table, LARGE, Normal. I even tried to assign the number of sectors and cylinders manually but its no use. I tried to install LILO and i got another error during configuration so im stuck there now. I dont know if its a BIOS problem, a HDD problem or a Motherboard problem.

We could stay in touch just to see if one of us gets the definitive solution. Its not nice to have to reboot the machine 10 times before it manages to boot the OS correctly! XD

---

### Post by psusi on 2007-05-24
If your bios supports LBA then it should be able to see the whole disk.  Please paste the output of sudo fdisk -l, and the contents of your /boot/grub/menu.lst file.

---

### Post by steamshooter on 2007-05-24
When I type sudo fdisk-|  I don't get anything, just a blinking curser.

---

### Post by psusi on 2007-05-24
That's odd... how about sudo fdisk -l /dev/sda or /dev/hda?

---

### Post by steamshooter on 2007-05-24
ubuntu@ubuntu:~$ sudo fdisk-|/dev/sda
bash: /dev/sda: No such file or directory
sudo: fdisk-: command not found
ubuntu@ubuntu:~$ sudo fdisk-|/devhda
bash: /devhda: No such file or directory
sudo: fdisk-: command not found
ubuntu@ubuntu:~$



Am I doing something wrong?

---

### Post by psusi on 2007-05-24
That's a lower case L, not a pipe ( | ).

---

### Post by steamshooter on 2007-05-24
Sorry bout that. I thought it was a pipe. Still no-go.



ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk-l/dev/sda
sudo: fdisk-l/dev/sda: command not found
ubuntu@ubuntu:~$ sudo fdisk-l/dev/hda
sudo: fdisk-l/dev/hda: command not found
ubuntu@ubuntu:~$

---

### Post by steamshooter on 2007-05-24
ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         854     6859723+   7  HPFS/NTFS
/dev/hda2             855       16267   123804922+   f  W95 Ext'd (LBA)
/dev/hda3   *       16268       19457    25623675   83  Linux
/dev/hda5             855        2001     9213246    7  HPFS/NTFS
/dev/hda6            2002        6933    39616258+   7  HPFS/NTFS
/dev/hda7            6934       14766    62918541    7  HPFS/NTFS
/dev/hda8           14805       16174    11004493+  83  Linux
/dev/hda9           16175       16267      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$




This is what you're looking for. I'm not sure what I did different but it worked:)

---

### Post by psusi on 2007-05-24
My goodness you have a lot of partitions.  Please describe the intended purpose of each one, and post the contents of your /boot/grub/menu.lst file on your hard disk.

---

### Post by dstew on 2007-05-24
The command is ```
sudo fdisk -l
```Mind the gap between **fdisk** and **-l**.

EDIT:OK, beat me to it.

The simplest, most straightforward way to get your system installed is to use a /boot partition. First, shrink your XP partition to give you 100 mb of unallocated space at the left end (beginning) of the drive. GParted, which you can get [here]("http://gparted.sourceforge.net/livecd.php"), has a Live Cd that will boot, and let you do the partitioning. It will safely shrink your XP partition. (Vista is different -- use the native Vista volume manager tool to shrink Vista partitions).

Once you have the unallocated space there, re-install Ubuntu. Create a new partition out of that 100 mb space, format it ext3. Also, make it a primary partition. When you get to the point where you choose mount points, select /boot for the 100 mb partition. You can install the rest of Linux (root and swap) just like you did before.

---

### Post by steamshooter on 2007-05-24
psusi,

/dev/hda1 - XP partition - C: drive- 6.54gb
/dev/hda2 - Not real sure where that came from. It didn't show up in XP- 118.07gb
/dev/hda5 - XP programs and documents -D: drive- 8.79gb
/dev/hda6 - MP3s -E: drive- 37.78gb
/dev/hda7 -F: drive - Where I convert analog music to digital - 60gb

The rest I'm trying to give to Ubuntu. This is only supposed to be 160gb. Now I am really confused.

According to GParted
/dev/hda1 has a triangle with an exclamation point ( ! ) beside it.
/dev/hda2 is an extended partition and it has a lock on it.


I don't know how to give you the contents of my  /boot/grub/menu.lst file.

dstew,

That's exactly what I want to do. I don't know how to shrink my XP partition to the right to free up 100mb or so at the beginning. GParted is only letting me take free space off the end of the partition instead of the begining.

I've made a mess of it.. Can it be sorted out?

steamshooter

---

### Post by psusi on 2007-05-24
Ok... /dev/hda2 is an extended partition which contains 5 and up.  

What are partitions 3 and 8?  They are both Linux partitions, but which one did you install ubuntu to and what is the other for?

---

### Post by steamshooter on 2007-05-24
I'm not sure. I was trying to make one partition for Ubuntu and one for swap. I don't know how it ended like this. /dev/hda8 is showing 296.92mb used and /dev/hda9 is showing 521.09mb used plus boot. Time to start over?

steamshooter

---

### Post by psusi on 2007-05-24
Yea, sounds like its' time to start over.

---

### Post by cox377 on 2007-05-25
You got me there with having XP as well

I will try and remember tonight to look at my layout because i know this problem nearly brought me to tears haha.

CoXen

"I suggest you create 128MB /boot, memory-size swap, 16GB / and the rest for /home"

All Primary EXT3

This is exactly how i had it and it worked fine.

---

### Post by steamshooter on 2007-05-25
I re-installed. Got my hard drive straightened out. Still Error 18. I can't get GParted to access my first partition (with XP on it -NTFS). I've got a triangle with an exclamation point in it. It won't let me re-size it. 

How do I get into GParted to shrink this first partition to install GRUB at the beginning of the hard drive?

I must go to work. Will check back later tonight.

Thanks for your help
steamshooter

---

### Post by dstew on 2007-05-25
I think you can shrink the partition from the right, then move the whole partition over to the right to give you the space you need. GParted can do both at the same time, but it might be best to shrink first, let it complete, then move it over. The triangle might mean that the partition is mounted, or that there are bad sectors on the partition. To check it for errors and fix them, you need to use the windows **chkdsk** program with the /f switch. You can get it on the [Windows Recovery console]("http://support.microsoft.com/kb/314058"), from the recovery CD. And of course, you have defragmented the partition, right?

One more thing: if you see immoveable green bars on the partition display, these are Windows "swap" files, also called page files. If these are keeping you from shrinking the partition, you have to disable the page files from within Windows, defragment again, and then shrink.

---

### Post by psusi on 2007-05-25
How do you currently have your bios set up?  It needs to be set to LBA mode and AUTO type.

---

### Post by steamshooter on 2007-05-25
My BIOS settings are:

Type: Auto
LBA/Large Block: On
Block Mode: On
32 Bit Mode: On
PIO Mode: 4

Here is my hard drive:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         854     6859723+   7  HPFS/NTFS
/dev/hda2             855       14675   111017182+   f  W95 Ext'd (LBA)
/dev/hda3   *       14676       19457    38411415   83  Linux
/dev/hda5             855        2001     9213246    7  HPFS/NTFS
/dev/hda6            2002        6933    39616258+   7  HPFS/NTFS
/dev/hda7            6934       14582    61440561    7  HPFS/NTFS
/dev/hda8           14583       14675      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$


Would reading through this help me any?
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Would it be practical to install GRUB on a 2gb hard drive set up as master and use the 160gb drive as slave? 

And use the remainder of the 2gb drive for swap file?

Thanks
steamshooter

---

### Post by psusi on 2007-05-26
Hrm.... well, you can try reinstalling grub and forcing it to use lba and see if that helps:

```

sudo grub
root (hd0,2)
setup --force-lba (hd0)

```

If that doesn't help then there must be something screwwy with your bios.  You should still be able to get it working though if you create a small ( 100 mb ) /boot partition at the start of the disk.

---

### Post by steamshooter on 2007-05-26
I forced GRUB into LBA. It succeded but, still error 18.

This is what GParted is telling me:


"Information about /dev/hda1

/dev/hda1
6699MB

Filesystem:    ntfs
Size:              6.54 GB
Flags:          

Path:             /dev/hda1
Status:         Not mounted

First Sector:    63
Last Sector:     13719509
Total Sectors:    13719446

Warning:
Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
Did you install the correct plugin for this filesystem?"


I am unable to resize this partition. Maybe this has been the problem all along?
I have no idea what the correct plugin is or where to get it.
I did check the checksum before I burned the CD and have run the built in integrity check on the CD before I installed.

---

### Post by dstew on 2007-05-26
You will need to create a small /boot partition at the beginning of your disk. GParted is telling you the file system has errors on it. Before you can shrink your partition, you need to run **chkdsk /f** from the Windows recovery console to try to repair the file system on that partition.

---

### Post by steamshooter on 2007-05-26
OK, that's what I will do. Do I need to run "fixboot" or "fixmbr" to restore the boot for Windows, then download GParted Live CD to do this? I'm sorry to be asking such elementary questions. (XP is still new to me) 

I'm thinking I need to :
1) Run recovery console -fixboot or fixmbr to get XP up and running again so I can get online.
2) Download GParted Live CD.
3)Make my 100MB /boot partition for GRUB
4)Study up on GRUB so I can install it on the 100MB partition.
5) I'm pretty sure Linux is just sitting on my hard drive waiting for me to access it. Do I need              
   to re-install again?

Hopefully I'll get this thing figured out soon. I want to try out my new Ubuntu Linux!

Again
Many thanks for your help
Steamshooter

---

### Post by dstew on 2007-05-28
Your plan is essentially correct. While you are in the Windows recovery mode, don't forget to run **chkdsk /f** to get your disk fixed. Once you have Windows booting, turn off the page file in Windows, and re-defragment. Even though you have Ubuntu in there, you will have to reinstall it once you make your /boot partition, because the partitioning scheme in your current install has the /boot directory in the root partition of Linux. Well, maybe you can make the /boot partition and copy over to it everything in your linux /boot directory, but then you will have to custom install grub to boot from the /boot partition. But, this can be done. Maybe it would be fun to try to get it to work without installing again. It depends on how adventurous you feel.

Not adventurous -- install anew. Adventurous -- try to move /boot and reinstall grub.

p.s. did I spell "adventurous" correctly?

---

### Post by steamshooter on 2007-05-31
I sit here typing this from my new Ubuntu system! (Look Ma, no live cd!)

I managed to really booger up my XP partition to the point I was getting all kinds of big time errors. So...I wiped it out, installed 98, then installed Ubuntu and everything is fine. Apparently XP doesn't play nice with Linux. Win 98 could care less where Grub is. Or maybe it's the other way around. Anyway I'm happy. 

Thanks for all your help. As I get more into this, I'm sure I'll have lots of questions. I want to eventually end up in Ubuntu Studio, but, I've got to learn some basics first. 

All hardware has been recognized with the exception of my Midman Audiophile 2496 soundcard. (I know Alsa's got the driver, I haven't had a chance to do it yet)

Again many thanks
Steamshooter :D

---


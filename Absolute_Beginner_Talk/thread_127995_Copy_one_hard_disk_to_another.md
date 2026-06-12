---
title: "Copy one hard disk to another?"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by fairdoes on 2006-02-10
I've set up Breezy, and after only a week it runs like a dream. I've spent ages downloading extra applications (on dial up connection) and would really like to backup the whole hard drive to another. Any ideas?

If anything goes wrong, swapping to the backup drive will save the servers' bandwidth as well as my time. Thanks.:cool: 

It's a dual boot at the moment, but the Windows bit doesn't really matter:evil:

---

### Post by gingermark on 2006-02-10
If you can afford the disks, then RAID might be an option. I haven't implemented it myself, but it is my understanding that any changes to one disk are reflected in another. A page about it is here: [http://linas.org/linux/raid.html](http://linas.org/linux/raid.html) - although that one does seem to be orientated towards a system administrator.

If you are just looking to backup the packages you have downloaded and installed, I believe there is a way to copy them to a CD, and use that CD as an extra repository. That way might well be more appropriate. Have a look at [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto) for more info on that.

---

### Post by mips on 2006-02-10
You can use the dd command, very simple. It allows you to mirror to a drive or an image file.

WARNING!!!: Make sure you do NOT confuse the source & destination drives else you will loose everything.

---

### Post by Davyp on 2006-02-10
If you just want to do regular backups then a couple of options are tar and cpio. Both of these programs allow you to do incremental backups, meaning you can add your new data to your existing archive. Both can be easily compressed using bzip2 or gzip. Tar is easier to use, but cpio is a bit more sophisticated.

tar -xzvf myarchive.tgz /
(the z flag compresses it with gzip, if this were a j it would use bzip2)

find / -depth -xdev | cpio -o -v -F myarchive.cpio
gzip OR bzip2 myarchive.cpio

---

### Post by Herman on 2006-02-10
> I've set up Breezy, and after only a week it runs like a dream. I've spent ages downloading extra applications (on dial up connection) and would really like to backup the whole hard drive to another. Any ideas? 
[http://rute.2038bug.com/index.html.gz]("http://rute.2038bug.com/index.html.gz")

Look up 18.5.4 'Duplicating a Disk' (in the link above).

The author is copying from hdc to hdd, so I wonder how many hard disks are in the machine. Perhaps the operating system being used is on hda [COLOR=Sienna](and hdb would be the floppy drive. So hdc and hdd can be unmounted and be worked on, they must be another two hard drives. EDITED)[/COLOR]
If I were doing this I think I would use a live CD and run off that, umount hda and hd[COLOR=Sienna]c[/COLOR] and modify the code accordingly. [COLOR=Sienna](Or whatever the right disk numbers are for the system being worked on).[/COLOR]
I don't understand why both disks need to be the same size, for sure there is a lot I don't know yet about things, maybe something to do with disk geometry? I would have though the disk being copied to could be equal sized or larger, but that's not what the instructions say. Someday I will try it myself and find out.

I do very often use [GParted livecd-0.2]("http://gparted.sourceforge.net/livecd.php"), and in the past I have used the Ubuntu installer CD's partitioner, and also Parted (CLI) to copy operating systems around from place to place on one hard disk and that works fine for me. I have tested that well, I do it often.
 I imagine you should be able to do the same thing with two hard disks using your favorite partitioning software. That's another thing I would need to try out myself and find out for sure. :-D (Herman)

---

### Post by fairdoes on 2006-02-14
Thanks everyone, I've printed your suggestions and will have a play. You seem to have covered present needs and a few possibilities for further down the road.

 I don't fancy RAID - If I mess up one drive, i've messed them both! Overwriting only files that have changed (indremental) sounds perfect, and reminds me of xcopy which I still use on my offline comp for massive WAV files (Linux doesn't have a version of Cubase yet!).

 I'm really impressed with the partitioner on the install CD - I can see why servers love unix. I found an old disk and made several partitions, formatted them different ways, and loaded 3 different operating systems (FAT, ext3, NTFS) and they all work. Linux had to be last, or XP declared itself the only boot option (typical).:p 

I tried **man dd** and it looks equally promising.

Thanks;)

---

### Post by patrick295767 on 2006-02-14
[QUOTE=mips]You can use the dd command, very simple. It allows you to mirror to a drive or an image file.

WARNING!!!: Make sure you do NOT confuse the source & destination drives else you will loose everything.[/QUOTE]
   
**dd** is the key of everthg !! 
This function is very powerful and allow you to copy all kidn of devices ... all kind of partitions (even different than both windows and linux).

An example : dd if=/dev/sda bs=512 skip=1 | dd bs=1024k | dd of=/dev/sdb bs=512 seek=1

[http://www.cpqlinux.com/dd-resize.html](http://www.cpqlinux.com/dd-resize.html)

Greetz

Patrick

---

### Post by fairdoes on 2006-02-15
Thanks Patrick - Nice aviator!:D

---

### Post by cotcot on 2006-02-15
If you do not have enough disk space to dd then you could consider "partimage". This is a clone for Nortons Ghost.  It allows you to image partitions and set them back. I use it to backup to a USB HDD. This requires a liveCD supporting partimage to USB 2.0. Therefore i use the Kanotix liveCD (it is debian based).

---

### Post by fairdoes on 2006-02-16
Thanks cotcot, disk space isn't a problem - when people throw out computers, I salvage the bits!:rolleyes:

---

### Post by fairdoes on 2006-03-16
Hi again!

 I've copied one disk to another using the partitioner on the ubuntu install CD. It copies all existing partitions (if you want to) so the new disk is multiple boot. All the work I've done setting up passwords, installing updates, etc, is all saved to the new disk.
 The new disk offers all partitons (both disks) as boot options! This seems to give me a choice of six!! (2 kernels of Ubuntu and Win98 on each disk).

I think I've got a good copy!

thanks all.:-D

---


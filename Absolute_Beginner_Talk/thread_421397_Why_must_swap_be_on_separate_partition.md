---
title: "Why must swap be on separate partition?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-04-24
This is separate from my help question (that I haven't been able to solve yet, so please help if you can--see link below).  Why must the swap drive be on a separate physical partition?  If you're on a one hdd system, this forces the read head to swing across the disk if your swap is at the end of the disk and your files at the beginning.  This not only slows accesses down but creates extra wear and tear on the hdd.  It seems like a fixed size swapfile at the front of your OS partition would be more beneficial to performance since when it needs to be hit, it's very close to your files, so reduced travel distance for read head and faster accesses.  Is it possible to configure Ubuntu to do this?

I need help on this topic:
[http://ubuntuforums.org/showthread.php?t=420879](http://ubuntuforums.org/showthread.php?t=420879)

Thanks in advance.

---

### Post by igknighted on 2007-04-24
> **timzak said:**
> This is separate from my help question (that I haven't been able to solve yet, so please help if you can--see link below).  Why must the swap drive be on a separate physical partition?  If you're on a one hdd system, this forces the read head to swing across the disk if your swap is at the end of the disk and your files at the beginning.  This not only slows accesses down but creates extra wear and tear on the hdd.  It seems like a fixed size swapfile at the front of your OS partition would be more beneficial to performance since when it needs to be hit, it's very close to your files, so reduced travel distance for read head and faster accesses.  Is it possible to configure Ubuntu to do this?

I need help on this topic:
[http://ubuntuforums.org/showthread.php?t=420879](http://ubuntuforums.org/showthread.php?t=420879)

Thanks in advance.

This is partially because you don't want to have the rapid read/writes required for swap on an ext3 partition.  The swap partition format handles those operations better.  Also, if you only have one HD and are worried about this you could pick up a USB thumb drive, format it swap and use that instead.  Personally, I never use my swap.  I just wastes 1gb of my HD space, as I never fill 1gb of ram.

---

### Post by lamalex on 2007-04-24
because swap is a completely different file system than ext3. you can't have a partition with more than one file system.

---

### Post by timzak on 2007-04-24
> **Iamalex said:**
> because swap is a completely different file system than ext3. you can't have a partition with more than one file system.

Ahhh...that makes sense.  So can you put the swap partition at the front of the physical drive, ahead of the OS partition?  That seems like it would keep the read head closer to your data if it ever has to go to the swap.  Also, do you have to have a swap?  Like igknighted said, if it's not being used, can it be disabled?  Or at least make it a minimum size.

---

### Post by compmodder26 on 2007-04-24
You should have a swap partition.  The size depends on the amount of RAM you have and the perceived amount of load you think you'll be putting on it.  I have 1GB of RAM on my laptop and swap hardly every gets used.  However, if I was to start playing 3D games, I think that swapping would happen more frequently.

The general rule of thumb is to have swap be about 1-2x the amount of RAM you have.  I would say this is applicable for <= 512MB of RAM.  Above that (in my experience), anything more than 512MB of swap really isn't needed (unless you are doing CPU intensive work).

---

### Post by psusi on 2007-04-24
Swap is not a filesystem at all.  It is the avoidance of using a filesystem that makes a dedicated swap partition faster than a swap file ( which you can use if you really want to ).  As for wear and tear on the disk, seeking a few more cylinders over does not stress the disk any more.  

You want swap on its own partition because it's faster as it bypasses the filesystem overhead.

---

### Post by anaconda on 2007-04-24
actually you dont need a swap partition. A swap file in your root partition is just as good. 

The problem is the liveCD installer, which wont install without a swap partition. You could always make the swap partition to a USB-stick just to be able to finish the installation with the liveCD. And then reformat the USB-stick later..

The alternate install CD lets you install without a swap partition.  

In my opinion a swap-file is BETTER than a separate partition. because it is very easy to adjust the size of a swap file. or add some swap if/when needed.

Some people say that a swap partition is faster than a swap file, because partition is mounted separately and accessed directly and that swap file would be accessed throug the file system (like it used to be done 10 years ago..), but now a swap file is also mounted in the fstab file, and it is accessed directly. so it isn't slower..

---

### Post by timzak on 2007-04-24
> **psusi said:**
> Swap is not a filesystem at all.  It is the avoidance of using a filesystem that makes a dedicated swap partition faster than a swap file ( which you can use if you really want to ).  As for wear and tear on the disk, seeking a few more cylinders over does not stress the disk any more.  

You want swap on its own partition because it's faster as it bypasses the filesystem overhead.

Mainly it just seems like it would slow things down if your hdd's read head was having to stop, jump all the way across the platters, do it's swap thing, then jump all the way back.  Keeping the swap physically closer to your data would minimize travel distance and thus reduce access times.

---

### Post by Steggy on 2007-04-24
You're perfectly able to use a swap file instead of a swap partition. It's generally not recommended, but it is possible.

I found some instructions on how to do so on the forums:
[http://ubuntuforums.org/showpost.php?p=287528&postcount=6]("http://ubuntuforums.org/showpost.php?p=287528&postcount=6")

---


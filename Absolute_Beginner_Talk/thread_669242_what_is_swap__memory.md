---
title: "what is swap  memory"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-01-16
where can i find  my other partions on my hard drive
i mean if my system os on c say
then wher i can locate my other drives
its very confusing

---

### Post by dgray_from_dc on 2008-01-16
In windows terms, swap memory is where linux puts its temp files.  It's the area of the hard drive that linux uses for scratch paper when doing calculations.

---

### Post by Cypher on 2008-01-16
In a command prompt type
```

sudo fdisk -l

```
You will see all the partitions on all of your HD's. Look for NTFS/FAT/VFAT file system types and those are your Windows partitions.

Linux does not using the C, D, E naming scheme which can be very restrictive..

SWAP is a special partition that is used by Linux when the available physical memory gets too low and new requests are coming from applications. It will take a bunch of physical memory and "swap" it to the harddrive and clear up the memory.

Needing to use the SWAP partition usually means that your system might not have enough memory for the task it is performing. If you do this long enough, the swapping back and forth from system memory to the HD ends up causing thrashing on the HD and will degrade performance..

---

### Post by Cypher on 2008-01-16
> **dgray_from_dc said:**
> In windows terms, swap memory is where linux puts its temp files.  It's the area of the hard drive that linux uses for scratch paper when doing calculations.
Not exactly. Don't confuse the swap partition with the "tmp" partition which is used temporarily for files. Any and other values are usually stored in system memory.

[Wikipedia]("http://en.wikipedia.org/wiki/Swap_space") explains more..

---

### Post by SunnyRabbiera on 2008-01-16
swap is very good if you use low memory like under 512, its a lifesaver

---

### Post by ARhere on 2008-01-16
> **coolnik6 said:**
> where can i find  my other partions on my hard drive
i mean if my system os on c say
then wher i can locate my other drives
its very confusing

Your question is very confusing.  But I am going to assume you are used to Windows where you see 'C:\  D:\ ... " as your "hard drives" and now do not know where to get your data on a Linux system.  This is normal confusion.  Remember you can click on a word that is highlighted to get an explaination of what that word is.

[Hard drives]("http://en.wikipedia.org/wiki/Hard_drive") are organized as [partitions]("http://en.wikipedia.org/wiki/Disk_partitioning").  A hard drive can have one or more partitions, depending on how you want your data organized.  In order for the operating system to use those partitions to store data, they must be [mounted]("http://en.wikipedia.org/wiki/Mount_%28computing%29").  Windows mounts a partition using a drive letter, this is a throw-back form the days of [DOS ]("http://en.wikipedia.org/wiki/DOS")in the 80's to 90's.  Linux (*and even windows 2K, XP, and Vista*) mount each partition as a folder within the operating systems files.  In Ubuntu, if you plug in a USB hard drive, the OS will mount the drive somewhere in '/media/<device>' and will normally place an icon on the desktop for you to access the data.
If you installed an internal hard drive, then the mount point might be in '/media/<device' or in a mount point you may have specified.  Look for a '/windows' folder in your filesystem if it is a disk used in a Windows OS.

The title of your thread said, "what is swap memory" and a link was given to explain this, but in short.  Swap memory is a place to store data in system memory (RAM) or programs that are not immediatly being used.  This is usually done when a new program is run and there is not enough RAM left.  Think of it as yourself reading several papers.  What you hold in your hand, reading, could be the 'RAM'.  But other papers you want to read, but are not currently reading, will lay on the desk that you can grab easily.  This can be seen as the Swap space.

If you wish to learn more, just ask!  But be specific on what you want to know.
-AR

---

### Post by macogw on 2008-01-16
> **dgray_from_dc said:**
> In windows terms, swap memory is where linux puts its temp files.  It's the area of the hard drive that linux uses for scratch paper when doing calculations.

No, in Windows terms its the pagefile.sys.  When Windows says stuff about "virtual memory" (like that you've run out and it's increasing the maximum), it means that all of the physical memory is use and now it's using the hard disk as "virtual memory"--pretending it was RAM.  Swap is what Linux uses as pretend RAM when you have so much stuff running that your physical memory can't hold it all.

---

### Post by Sef on 2008-01-16
If you have a gb or more of ram, then swap really isn't necessary.  Usually you make your swap 1 1/2 times your ram, but no more than 1 gb.

---

### Post by ARhere on 2008-01-16
> **Sef said:**
> If you have a gb or more of ram, then swap really isn't necessary.  Usually you make your swap 1 1/2 times your ram, but no more than 1 gb.

I am sorry but that is not true, in a windows machine.  I might be wrong on a Linux machine, but I do know from experience that a Windows XP machine, with 2GB of RAM, will completely freeze up after a few  minutes of use without a Swap file set.  Like I said, this might not be so in Ubuntu but I doubt it.

The reason is, caching.  If you have free memory while Ubuntu or Windows is running, I know the OS will grab the avalible memory to cache commonly used files.  **The reason I said Ubuntu and not Linux** is I am sure there are a lot of Linux distro's, including embedded Linux, that do not behave in this fashion.

-AR

---

### Post by macogw on 2008-01-16
> **ARhere said:**
> I am sorry but that is not true, in a windows machine.  I might be wrong on a Linux machine, but I do know from experience that a Windows XP machine, with 2GB of RAM, will completely freeze up after a few  minutes of use without a Swap file set.  Like I said, this might not be so in Ubuntu but I doubt it.

The reason is, caching.  If you have free memory while Ubuntu or Windows is running, I know the OS will grab the avalible memory to cache commonly used files.  **The reason I said Ubuntu and not Linux** is I am sure there are a lot of Linux distro's, including embedded Linux, that do not behave in this fashion.

-AR

On Linux, there is caching as well.  However, you are unlikely to need any swap if you have 1GB of RAM under "normal" circumstances, but if you have a lot of memory-hungry apps going at once (Compiz, Firefox, keeping a game on pause while watching a movie and all that running...) then you might need some swap.  Swap only is used when you run out of physical memory though.

Tradition says you take the physical amount of memory and multiple by anything in the range of 1 to 2, and that's how much swap to have.  That tradition comes from the days when you had 16MB of memory.  You're unlikely to use much swap when you do use it, and it's better to just plain avoid swapping because it's so slow (RAM is very fast, hard disk is very slow).  You need to have at least as much swap as you have RAM to be able to hibernate, since in that case the contents of memory is written to the swap partition.  If you have less swap than memory, that can't happen.  A little bit more might be better in case you are swapping when you hibernate.  If it's a desktop or you just plain don't use hibernate, you could just put like 256MB of swap because with 1GB of memory you're probably not going to need more than that (though you know your usage habits better than I do).

---

### Post by tigerplug on 2008-01-16
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)
[http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)

---


---
title: "Reformatting my 2Gb flash drive in something OTHER than Gparted."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-12-13
I was told to use Gparted. The thing sucks (at least on my PC) because it scans and scans and scans and never stops scanning. Oh well, whatever. 

So is there another way I can reformat my flash USB drive to a FAT32?

---

### Post by papuccino1 on 2007-12-13
Ok, I plugged it in and it shows this:

[IMG]http://i4.tinypic.com/6t3apau.png[/IMG]


And when I click on it to open it:

[IMG]http://i10.tinypic.com/6jz46f5.png[/IMG]


So is reformatting the way I should go? I'm not sure anymore?

---

### Post by papuccino1 on 2007-12-13
So um... anyone out there? :P

---

### Post by L Campbell on 2007-12-13
> **papuccino1 said:**
> I was told to use Gparted. The thing sucks (at least on my PC) because it scans and scans and scans and never stops scanning. Oh well, whatever. 

So is there another way I can reformat my flash USB drive to a FAT32?

I had a major problem with my flash drive but it works well now.

Here is the thread:-  [http://ubuntuforums.org/showthread.php?t=638987](http://ubuntuforums.org/showthread.php?t=638987)

Basically I used Gparted to create a partition then, because I wasn't real sure what I was doing, I put the partitioned flash drive in an XP 'puter and formatted it.  It seems to work properly now.

Hope this helps you.

---

### Post by asmoore82 on 2007-12-13
you can find out why GParted is getting stuck if you run it from a terminal ...
```
$ gksu gparted
```

Usually, it is because you have a legacy floppy drive and it is searching for a disk in that drive.
to work around this, you can specify a device for it on the command line:
[your flash drive will be *sdX* where *X* is a variable *letter*]
```
$ gksu gparted /dev/sda
```
If you have SCSI or SATA devices, the flash drive will be pushed down the alphabet,
you can view the output of `**dmesg**` to know for sure.

---

### Post by niteshifter on 2007-12-14
The screenshot you posted shows as a SanDisk U3 Cruzer Micro. I think that's your problem: U3 flash drives are problematic with Linux: automount fails. You might be able to mount the non-CD partition manually. You won't be able to mount it if that partition is U3-encrypted.

You can remove the U3 aspect from the device - but you'll lose U3 functionality with Windows.

This site features a removal tool, but you'll need a Windows PC to do it:
[http://www.u3.com/uninstall/]("http://www.u3.com/uninstall/")

The Widipedia page on U3:
[http://en.wikipedia.org/wiki/U3]("http://en.wikipedia.org/wiki/U3")

---


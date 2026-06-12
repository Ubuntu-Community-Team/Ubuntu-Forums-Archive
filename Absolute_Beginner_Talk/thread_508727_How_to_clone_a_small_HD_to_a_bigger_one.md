---
title: "How to clone a small HD to a bigger one?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-07-24
So now I have both Xubuntu and Windows 2000 working perfectly. The problem is Xubuntu is on a 4 giga Hd and windows on 10 giga Hd.

So the question is: How do I copy the entire Hd contents to a bigger one? I think people refer to this a cloning. I tried to copy all the files manually from windows to the bigger Hd but it gives errors and the system wont start: Haven't tried yet to copy all off the xubuntu files, but I expect it wont work either.

It took me some time to put both systems as I wanted them to be. so a new install will mean a lot of wasted time. Is there an easy way to clone the smaller Hds to bigger ones?

In windows aparently there are some shareware programas wich might do this. Haven't tried them yet. Is there a simpler way to to this in linux?

---

### Post by Dan Hammond on 2007-07-24
there is a program cvalled clonezilla, try to find it on google i think it may be a disk image like ubuntu to be used as a bootable disk, alternatively you could just format the larger hard drive to ext3 and use it as your home directory

---

### Post by benx009 on 2007-07-24
[BootIt NG]("http://www.terabyteunlimited.com/bootitng.html") can create an exact image of any partition of your disk and copy it to a partition of another internal or external (USB) harddrive.  of course, if you wish to do this, you will have to adjust how your system boots accordingly

---

### Post by dannyboy79 on 2007-07-24
this has been discussed in length within the forums. There are many different techniques. You could use the dd command which will copy bit by bit. You could use Partimage which would copy it by partitions and make an image of each partition. You could Ghost4Unix or Ghos4Linux.

If you're somewhat of a beginer, I would suggest using the dd command. Here's a little write up on it:
[http://www.netadmintools.com/art165.html](http://www.netadmintools.com/art165.html)

Note, if you have 2 hard drives (1 w/ Ubuntu, and 1 w/ Windows), the dd command will really only work to get one of the harddrives onto the new one. You can't then do the other hard drive as it will erase what you did the first time. You'll have to look into a tool that copies just the windows partition into an image (like partimage), then prepare the new partition from within Ubuntu, then use part image to restore the windows image onto the new partiiton. BUT partimage writing onto NTFS drives is still in Beta so you may want to look into another certified way to transfer data for NTFS drives.

 System Restore is an invaluable tool, check it out:
[http://martybugs.net/linux/image.cgi](http://martybugs.net/linux/image.cgi)

---

### Post by asmoore82 on 2007-07-24
i think you are looking for the 'dd' utility, see ...

```
~ $ man dd
```

in short ....
```
 ~ $ dd if=/dev/hda of=/dev/hdb
```
will clone hda to hdb IFF hdb is the same size or bigger

and BTW everyone out there you can place a CD in your drive, do not close the tray, and ...
```
~ $ dd if=/dev/cdrom of=mycd.iso
```
to make a quick image of a CD ;)

P.S. if and of == input file and output file

P.P.S. you may note that the 'dd' command does not require/like neither a dash nor double-dash in front of its options like so many other command line utilities does ... this is because 'dd' is sooo old it actually predates those command line conventions.

---

### Post by Ganda_Melga on 2007-07-24
Hum.... It's kinda tricky. But I'll give it a shot. Thanks a lot to all the people who replied my question. :popcorn:

---

### Post by alienexplorers on 2007-07-24
This may sound like a easy way out, but when I got bigger drives I just did brand new loads of both programs.  This way I started with a clean install without all the junk I loaded and earsed over time.  I did though back up all important information so I would still have it if needed.

---


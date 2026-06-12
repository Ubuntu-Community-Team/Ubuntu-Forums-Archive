---
title: "Dual boot install partition / boot questions!"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by garidisk on 2007-04-24
Hello everyone!
I am planing  to install Ubuntu 7.04 on my pc (P4 @ 2.4GHz, 512 MB)  and make it dual boot so that i can use WinXP as well!  I have a partition of 40GB which i plan to divide in the following :
1. 1GB swap
2. 20GB WinXP
3. 19Gb Ubuntu
I've read the sticky links but I have some things I'd like ask..so here goes : 
1. Should I create a seperate partition in FAT32? How much should that be and how can that come in handy?
2. Are the above partition sizes enough? Should I resize them?
3. When i boot I'll get the linux boot screen. I heard that if I at some point I uninstall Ubuntu, then I won't be able to boot directly to WinXP or I won't be able to boot at all! I heard something about linux creating a boot record of their own which remains even after I format the disk! It sounded a bit crazy to me but I had to ask ..;)
Anyway, that's all I can think of now!
Thanks in advance!

---

### Post by freebird54 on 2007-04-24
You have a pretty good idea about what's going on.  The main thing I would change is the orfer of those partitions.  It is easier (for Windows) if Windows is the first thing out of the box.  IN fact - it is easiest if you put Windows on the computer first - taking the amount you specify if you want that much.  There is a case to be made for leaving a smaller partition for each, and creating a shared partition - but it is not necessary.

When Ubuntu is loaded on, it WILL overwrite the MBR (Master Boot Record).  This only becomes an issue if you subsequently delete the Linux partition.  Easily 'fixed' though...  Once your Windows id up and running, make a floppy recovery disk with it, so you can restore the MBR.  IF you don't, there are stil lots of ways to do it.

Hope this helps!

---

### Post by xeth on 2007-04-24
hello,

I'm also trying dual boot. My 1st time is I installed Ubuntu first and use the partition manager included with the cd. When I was finished partitioning there was like 4 partitions. 2 main partitions that I set and 2 other that was 1.2GB each. I think that was the swap partition or something? Then I installed windows xp, the system was kinda wacked because the windows drive letter was E:!

So now I reinstalled windows xp first this time. 

Can I use the partition manager of ubuntu to repartition the system without reformatting windows?
Because the partition of ubuntu says that if I use it, previous partitions will be deleted or something to that extent. 

I can't find any definitive guide.

---

### Post by freebird54 on 2007-04-24
It doesn't do anything too drastic unless you tell it to use the whole drive!  The best idea is to put XP on, making its own partition to the size you want to give it.  Then let Ubuntu do its thing, or you can do manual mode if you want to be SURE what it's doing.

The nice thing is that it will pick up the Windows setup, allow dual booting to it automatically, and even let you see the drives from Linux.  Can't get much better than that!

EDIT:  should add this in I guess - miught make things clearer
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by garidisk on 2007-04-24
Thanks for the help freebird54!
I still don't know if i should create a FAT32 partition or not..! If I don't will my linux be able to read some files I have on the XP partition? What are the pros and cons in creating a FAT32 partition?
I guess for the files I want to move I can use my 2 GB USB stick but it should be easier if there was a partition where I can throw stuff in :)
Do the sizes seem ok? More space for Ubuntu or is it ok?

---

### Post by freebird54 on 2007-04-24
Sizes are fine.  Ubuntu can read the stuff direct from the Win partitions anyway - so there's always more storage if you want it :)  

The upside of a  FAT32 partition is that both sides can read and write it for sure.  The downsides are all the reasons that no one uses them anymore (fragementation, speed, wedged-in long flename support etc).  As Windows (XP/2000 and beyond) can load a R/W driver for ext3 (Linux partition) and Linux can load ntfs-3g for NTFS (standard win partition) now, I wouldn't myself.  :)

---

### Post by garidisk on 2007-04-24
Thanks again!
I'm hopin my next message will be from firefox in ubuntu :)
One last thing..with the ntfs-3g for ubuntu and the ext3 driver for winxp I'll be able to write and read in both the file systems?!

---

### Post by xeth on 2007-04-24
So while windows is installed I can use the live cd and use it's own partition.
I've already defragged my hd
In the menu I choose the first installation, it will automatically resize the ntfs partition without destroying the windows installation? 
My only concern is that when I partition using the ubuntu live cd is that I won't have to reinstall windows again.

Because in windows a while back I tried a software partitioner and the whole system was deleted somehow.

---

### Post by kpel on 2007-04-24
> **garidisk said:**
> 
One last thing..with the ntfs-3g for ubuntu and the ext3 driver for winxp I'll be able to write and read in both the file systems?!

Correct.  I only use Windows for gaming now so I haven't bothered to install the ext3 driver.  I did install the ntfs-3g driver in Ubuntu so that I could move files over to the Windows disk if I needed to (patches, drivers, etc).  The other nice thing about *not* installing the ext3 driver in Windows is that Windows XP won't be able to see ext3 formatted drives so I don't have to worry about Windows messing anything up on me. ;)

---

### Post by Duck2006 on 2007-04-24
[http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot](http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot)

This may help

---


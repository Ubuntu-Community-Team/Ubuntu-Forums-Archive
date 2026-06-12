---
title: "sizing partitions during install"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by ramster on 2007-01-31
Sorry but i still cant get on ubuntu. cds 6.06 from Official Ubuntu Book and Ubuntu Linux for Non-Geeks. Both give me partitions which I cannot change either by 'stretching' or replacing the numbers. Could it be because Mandriva is installed though I have overwritten it with Suse and rewritten again with Mandriva, in both cases a working system. Dual booting with windows but if I can get a linux system working properly (ISP is married to gates) I would dump windows.

---

### Post by mikewhatever on 2007-01-31
So, you're using LiveCDs. How exactly are you trying to resize, and which partition. Remember, you can not resize a mounted partition.

---

### Post by ramster on 2007-01-31
thanks mikewhatever for reply. On manually partitioning I get a similar screen to that in the book. Large rectangle in middle: /dev/hda1  nfts 9.82gb
                                               /dev/hda2         8mb
                                               unallocated
                                               /dev/hd3          94.3mb
Click on unallocated then NEW on to figure 2-6 in the book. 
                           minimum size 8mb                               maximum size 8mb
Using arrows only reduces the top picture. Putting in the numbers and pressing Add reverts back to 8mb. Just can't get past it!?
                                                        Sorry we can't get in touch quicker. My time zone, and responsibilities limit my attendances.

---

### Post by ramster on 2007-02-04
I'm about to give up on Ubuntu. Here is my drive
/dev/hda1           ntfs           9.85gb                5.31            4.55          boot
/unallocated   unallocated     7.84mb       
/dev/hda2          ext3          94.13mb             12.62mb      81.52mb
/dev/hda3       unknown      27.31gb                                                   lvm

Have discovered I have a drive (E:) mainly a friend's photos

 If I wish to retain windows can I just delete the other partitions and install new ones?
and what should I do with the E drive. I think it is part of the 37.27gb, not in the win part, at least when defragmenting.

Oh yes, Mandriva 2006 is on the disc, working but not really suitable.

                                                                      ramster

---

### Post by Mr. Eddy on 2007-02-04
wow, can you give a nice overview of your partitions and your disk as it is now? and then an overview how you would like is. what partitions do you want to save?

so now you have:

hda1 ntfs 9.85 gb (windows partition)
hda2 ext3
hda3 unknown ??

---

### Post by ramster on 2007-02-04
Thanks. Been downloading alternate cd. Hope friend can burn it for me. I even have trouble burning myself.
I just wanted to keep Windows (for now)  and make 2gb root, 256mb swap and 10 or 20gb  for home. The ones I've got won't change.

---

### Post by laidback on 2007-02-04
Please don't give up, Ubuntu is really worth the effort.

This link gives you a Live CD that runs Gparted:-

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

download the ISO and burn to a CD (I believe that it can be done in Windows as well)

With a Live CD running Gparted your main hdd wont be mounted so you'll be able to adjust the sizes etc. You must have unused space to left or right of a partition you wish to extend, otherwise there's no space to extend into. Gparted allows you to slide the partition left or right as well, but you cannot jump over another partition. I believe that Gparted is also on the live Ubuntu cd, in which case there may be no need for the download...not sure what happens to a swap file when using the live Ubuntu cd, if it's on hda then maybe it's mounted..this could be a problem, if so go the live Gparted route as above.

I use caddy discs, these allow me to change my hd as per a CD, I have several and install different distros on each one, or create a development Ubuntu hd so I can play with ideas without damaging my main Ubuntu installation, I use 6.06LTS mainly, but also have 6.10 on another HD.

As a Newbie I can state without fear of contradiction that Ubuntu really is worth the effort. Sorry to hear that you're having installation problems, but like you my main desire has been to distance myself from Old Bill, I have succeeded to the point where I simply don't use my XP pc anymore. I've been at it around 8 months.

Stick to your guns, the prize is worth the effort.

:)

---

### Post by ramster on 2007-02-08
Wish I could be laidback. Tried deleting partitions but they retain their size, apart from the 'balance' the biggest is 94mb and others 8mb. Haven't got the iso burnt yet but the book makes its use even harder. Why can I not get rid of the linux partitions on my dual boot computer? They are so small that I now understand why I don't like mandriva.

---


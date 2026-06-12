---
title: "Acessing the Linux Partition from OS X"
date: 2008-07-17
forum: Apple Hardware Users
---

### Post by Mattaus on 2008-07-17
Hi all,

I had a previous thread regarding installing Ubuntu using rEFIt. Well I got that working (after the whole freezing on the tux logo etc problems were sorted) but now I'm trying to figure out how to access the Linux partition from OS X (and hopefully vice versa)

I found this tutorial through the guide to installing Ubuntu on a Macbook Pro:

> Hi all! This is my first blog so I’ve though of sharing some info regarding accessing a Linux partition from a Mac and mounting it on OS X startup &#12484;

Install Mac Fuse - MacFUSE-Core-10.5-1.5.1.dmg
There’s an app for automating the proccess but it doesn’t work on Leopard, notice that you have to install it anyway! - [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)    

Simply Go to “Utilities” and open the “Terminal.app” , and type in : “sudo pico /etc/rc.common”    

Go down to the bottom of the file, and type in a new line the command: “mkdir /Volumes/Linux && mount_ext2 -o rdonly -x /dev/disk0s4 /Volumes/Linux”

where “/dev/disk0s4&#8243; - Its your linux partition
and “/Volumes/Linux” - Its your mount location

and to save the file press “CTRL+X” and type “Y” and press “ENTER”



I did that but it hasn’t worked. I actually just copied it word for word as I'm no good with partitions and what not. so the linux partition and mount location are quite probably wrong (I'm still learning!) Anyway - I installed Ubuntu EXACTLY as described in this tutorial: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) (second method with rEFIt) so even my partitions are exactly as listed in that tutorial.

So my question is, what should the added line on MY MBP look like? Another question is I noticed it mentions read only. Can this be changed so I can read and write to both disks in BOTH OS's?

Any help in regards to this matter would be muchly appreciated. I'll keep looking for a solution in the mean times.

Cheers.

---

### Post by schauerlich on 2008-07-18
/dev/disk0s4 should be /dev/disk0s3. That will point it to the 3rd partition on disk 0, which will be your ubuntu partition. Also, make sure that the directory /Volumes/Linux exists.

---

### Post by Mattaus on 2008-07-18
hmmmm, I did the ds03 thing but never checked if the Linux volume actually existed lol...I think it's been called 'UNTITLED'.

I've come up with an idea that I think suits what I want better - so I may skip this and ask another question in a new topic.

---

### Post by cyberdork33 on 2008-07-18
Just a suggestion, I wouldn't have the partition automounted on startup. Just mount it whenever you need to access something.

being able to write to the Ubuntu partition sometimes works and sometimes doesn't. The driver is a bit outdated and is all we have. The driver comes with a GUI app that you can use to mount/unmount the partition and stuff.

PS I don't know why it talks about installing MacFUSE. That is not needed for this at all.

---


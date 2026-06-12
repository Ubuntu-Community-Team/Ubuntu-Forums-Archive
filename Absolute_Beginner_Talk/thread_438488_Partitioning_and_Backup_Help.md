---
title: "Partitioning and Backup Help"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by oni5115 on 2007-05-09
I'm looking for some help on how to setup the partitions for a server box.    I've read around and the most of the guides seem to say to make  /  and /home, some add /usr.  One mentioned /var (since mail, MySQL, and http are started there).  Another said that apache used either /home or /usr for http.

I have a 120 Gb hard drive and no clue what paritions I should make.  I'm planning to use the box as a data backup and testbed webserver.

Long story short, I had a nightmare with FC6 and then found Ubuntu.  I had far less issues with my Voodoo 5 5500 card and RT61 chipset wireless card.  Because of the nightmare I had with FC6 I didn't want to bother with formatting the HD... after all, I had already locked up my system about 3-4 times while messing with the RT61 card, and had to reformat and install again anyways.  Why bother? :lolflag: 

Of course, since I didn't bother... install worked.  Found instructions on how to add gnome to server edition.  Found the guide to fix being stuck in 640x480.  Installed the RT61 drivers per the readme.  Things went fairly easily, or at least not so terrible that I gave up.

So now I am looking into backing up what I have and potentially repartitioning.  I've been looking around at backup utilities and from what I understand with Linux all I have to do is actually save the files.  I could simply tar the system, reinstall, untar and be where I was at.

I've run (excluding the incremental g):
tar -cvpzfg backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I plan to copy this to another machine for the time being.  Is this all I have to do to restore myself in case something happens?  Extract it all?

I've downloaded the gparted livecd (with clonezilla) and might also make a backup with clonezilla if it is really needed.  As mentioned above, I'm mostly curious how to partition the machine, or if I should even bother with it at this point.

On a side note, if I did add a /home partition would I lose everything in the current /home partition when it mounted the new partition?

---

### Post by apunc1 on 2007-05-09
> **oni5115 said:**
> 

I have a 120 Gb hard drive and no clue what paritions I should make.  I'm planning to use the box as a data backup and testbed webserver.

I would say with the size of your hard drive and for the purposes of a server, make separate partitions for these at the very least
/home
/boot
/var
/usr

edit: in addition to / of course. 

There are many tutorials on the internet that can help you with this. Here is a one i've found
[http://tldp.org/HOWTO/Partition/requirements.html](http://tldp.org/HOWTO/Partition/requirements.html)

This one explains partitions. [http://www.brunolinux.com/04-The_File_System/Primary_Extended_and_Logical_Partitions.html](http://www.brunolinux.com/04-The_File_System/Primary_Extended_and_Logical_Partitions.html)
You need to make an extended partition in which logical partitions can be under so you can have more than four partitions. It's better explained in the link :) 


> **oni5115 said:**
> On a side note, if I did add a /home partition would I lose everything in the current /home partition when it mounted the new partition?

If i'm correct in what you're asking, then this might help
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by oni5115 on 2007-05-10
Thank you, that last guide is exactly what I am looking for to make the transition smooth.  Now to figure out what sizes to make the directories.

I am considering the following:
/boot - 500 Mb
/ ~10 Gb
/home - ~75 Gb
/usr  ~10Gb (Current installation uses 1.5 Gb)
/var  ~10Gb (Current webserver on WinXP uses ~1.5 Gb)

These are just guesses really.  Sadly, the only guides I found that bothered to split beyond / and /home were for drives <20 Gb and written 4-6+ years ago. :(   Anyone with more experience in the matter have any advice on if the sizes are way too much, or way to small?

---

### Post by apunc1 on 2007-05-10
Those look pretty good to me. I've been looking at some more partitioning tutorials and there is a consensus about have a /tmp partition too, so you might want to consider that as well.

---


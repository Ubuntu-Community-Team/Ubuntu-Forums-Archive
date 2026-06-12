---
title: "creating new partitions"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by tjtansey on 2007-02-07
Ok here's the latest entry for the complete idoits guide to Linux.  I ran the Ubuntu set up cd and used the default partition setting which gave me a small swap and a reaaaally big root.  Here's the questions:  How do I add new partitions, and how do I designate file type ie FAT32?

Thanks

---

### Post by housam on 2007-02-07
Read this guide.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Zimmer on 2007-02-07
Are you dual booting with a Windows installation ?
If not, why the need for a FAT32 partition?

Read this for a bit of planning
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
and this for more detailed walk throughs. 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
I believe Ubunted uses GParted as the default partitioner utility.
As an idiot who has ponderd paranoically about partitioning in the past, I see it like this:

You decide what partitions you want before you install, you run the installer which asks you to format and partition the disk.(formatting, of course, wipes off all the data!)
 Create the desired partitions using the installer utility (GParted in this case) and then continue with the installation. 
 Then you live with what you have created until you are forced :)  to change by circumstance (new disk , new OS, new dual boot and so on.  ) The links I have given above are very good.....

---

### Post by tjtansey on 2007-02-07
Thanks, I decided after my WiFi fiasco that my new lifes work is going to be "The Complete Idiots Guide to Linux".  Me of course being the Idiot.  The reason I want to add the partitions are: I have a few winblows apps that I want to run on Wine.

---

### Post by carloslosgrande on 2007-02-07
[I]I've re-installed several times now and using the Gpart partioner from the Live cd is ok but limited.
I would strongly suggest you get the GParted cd from
[HTML]http://gparted.sourceforge.net/[/HTML]
and do a normal or auto install and then use the GParted cd to set up your partitions exactly as you want them.
In my opinion the GParted cd is far more powerful, ie it can do much more, and it works for dummies like me![/I]

---

### Post by tjtansey on 2007-02-07
Ok quick question:  I have my partitions set up as follows
/dev/hda1 ext3 5gb /
/dev/hda2 ext3 40 GB /home
/dev/hda4 linux-swap 6GB
25 GB unallocated (intend for this to be FAT32 for windows apps running with Wine

How do I unmount /home if I want to resize it?
Thanks

---

### Post by bodhi.zazen on 2007-02-07
Best to boot to a live CD and resize from there :p

Gparted is outstanding but the ubuntu desktop CD will work as well ;)

---

### Post by tjtansey on 2007-02-07
Thanks a bunch

---


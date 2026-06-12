---
title: "low disk space ...."
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-06-17
hey;
I have low disk space , about 6GB after removing many stuff, and i've read that Xbuntu is a good choice instead of Ubuntu in such case .... However, I really would like to install the Ubuntu dapper so;

1) what is the least disk space for dapper????

2) Is there any way to customise the Ubuntu dapper for low disk space during install????

thanks ....

---

### Post by glotz on 2006-06-17
1) The default install takes about 2,5 gigs.

2) You could install just the server version if you plan to install Xfce onto it.

---

### Post by mourad on 2006-06-17
2) You could install just the server version if you plan to install Xfce onto it.[/QUOTE]

what exactly is "Xfce" ?? and how to do this step (the server version then the Xfce) ??? and how much space this way will take ???

---

### Post by glotz on 2006-06-17
[Xfce](http://www.xfce.org/) is the desktop manager in Xubuntu. The server install will take [500 megs](http://help.ubuntu.com/6.06/ubuntu/serverguide/C/preparing-to-install.html).

---

### Post by u.b.u.n.t.u on 2006-06-17
Are you saying you have a 6GB HDD or 6GB left?

How much free space does your HDD have?

---

### Post by mourad on 2006-06-17
[QUOTE=u.b.u.n.t.u]Are you saying you have a 6GB HDD or 6GB left?

How much free space does your HDD have?[/QUOTE]


I have a 30 Gb hard disk of my laptop acer TM 290, divided into 2 partitions C and D ,I have Win XP on the C drive, and lots of stuff on the D drive, I emptied much from the D drive, leaving a space of about 6 GB for Ubuntu ...

---

### Post by catlett on 2006-06-17
6gb is plenty for Dapper. As long as you have the necessary processor/ram you should go with dapper. Xubuntu isn't necessarily smaller, it is for older system without much in the area of resources i.e. low grade processor and ram.

If you have a P3 at 800mhz or higher and 256 of higher mb of ram, go with dapper.

Go here first and download gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is a partitioner that runs off a live cd. Create 2 partitions out of D.  A 512mb partition that you format as linux-swap. The other make a 5.5gb that you format ext3.
Put in the install disk and run the installer. When you get to the partitioner select to manually set up the partition table. In front of the 512mb partition click on the box so the menu drops down. Choose "swap". Check off the circle next to it with the heading "format?". Next go to the 5.5gb partition. Select "/" for that partition's label. Check off the circle under "format?". Leave the other 2 partitions as they are. Dapper will mount them automatically. That's it. Let the installer run. It will put the entire install on the 5.5gb partition. You'll be left with between 2.5 to 3gb free. The 512mb will be used for virtual memory. (it is just like windows swap file. linux just uses a partition)
Enjoy

---

### Post by mourad on 2006-06-18
[QUOTE=catlett]6gb is plenty for Dapper. As long as you have the necessary processor/ram you should go with dapper. Xubuntu isn't necessarily smaller, it is for older system without much in the area of resources i.e. low grade processor and ram.

If you have a P3 at 800mhz or higher and 256 of higher mb of ram, go with dapper.

Go here first and download gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is a partitioner that runs off a live cd. Create 2 partitions out of D.  A 512mb partition that you format as linux-swap. The other make a 5.5gb that you format ext3.
Put in the install disk and run the installer. When you get to the partitioner select to manually set up the partition table. In front of the 512mb partition click on the box so the menu drops down. Choose "swap". Check off the circle next to it with the heading "format?". Next go to the 5.5gb partition. Select "/" for that partition's label. Check off the circle under "format?". Leave the other 2 partitions as they are. Dapper will mount them automatically. That's it. Let the installer run. It will put the entire install on the 5.5gb partition. You'll be left with between 2.5 to 3gb free. The 512mb will be used for virtual memory. (it is just like windows swap file. linux just uses a partition)
Enjoy[/QUOTE]

That is exactly what I was looking for, thank you so much Catlett ...I still need to figure out the steps of doing this ;
1) Does the gpart works from inside the windows, so that I partition the D before install Ubuntu ??? 

Would you be kind enough to show me how to do it a steps way (1, 2, 3 ....)

---

### Post by KarmaKing on 2006-06-19
I am runnnig Dapper on a P3 800 128MB and it runs fine.  It is a litle slow when opening certain programs (Arzureus, Add-Remove Programs), but performs quite well.

---

### Post by brenbart on 2006-06-26
Hah!  You want low disk space?

I installed Dapper 6.0.6 on a laptop with a 2GB hard drive.  I have 68MB of free space!

What can I delete?  

I already ran apt-get clean and apt-get autoclean.

---

### Post by glotz on 2006-06-26
Open synaptic and delete the fonts you don't need. There's some 300 megs worth of those. Also, you might want to get rid of any kernels you don't use. Also see [http://www.ubuntuforums.org/showthread.php?t=172661](http://www.ubuntuforums.org/showthread.php?t=172661)

---

### Post by brenbart on 2006-06-28
I don't see a way in Synaptic to delete fonts.  Is there something I'm missing?

---

### Post by glotz on 2006-06-28
Open synaptic. Select packages by status (lower left corner). Select installed. They are the ttf-something files. Right click > complete uninstall. *ttf stands for true type font*

---


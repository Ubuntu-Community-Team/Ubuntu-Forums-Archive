---
title: "Uninstall Ubuntu and Install Vista"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Koolgecko91 on 2008-04-01
Is there anything I will need to do so I can go directly back to Vista. Im doing a clean install and not saving anything on my laptop cause I dont have anything on it. I know about reformating but if im doing a clean install will i still need to reformat? I really like Ubuntu its just that my Dell doesnt run it very well.

---

### Post by Calash on 2008-04-01
I think the Vista disk should take care of it all.  You will have to delete the current partitions and create a new one, or ones depending on how you want to set it up.

If Vista cannot do it, the Ubuntu live CD will be able to, but try the Vista disk first.

---

### Post by Koolgecko91 on 2008-04-01
So no need to reformat. I used my entire 160 GB HDD for Ubuntu.

---

### Post by Calash on 2008-04-01
You will have to reformat, but before that you will want to repartition the drive.  When installing Vista you will get to the part where you select the drive and partition to install on.  There will be at least 2 partitions listed there, one is the Linux swap and the other is the root.  If I remember correctly you press D on them and they will be deleted

After that you select the empty space and let Vista work it's magic


Just a warning, this erases all the data on the drive...so be sure before doing it.

---

### Post by Koolgecko91 on 2008-04-01
So I wll do all reformating from within the Vista Install? I wont have to use a seperate disk?

---

### Post by Wim Sturkenboom on 2008-04-01
You should be able to do it from within Vista. I know MS does crazy things, but I doubt very much that they will be crazy enough not to provide a partitioning/formatting tool with their installer as one would not be able to install Windows in that case.

PS Create two partitions, one for OS (and applications) and one for data; don't make the first one too small.

---

### Post by Calash on 2008-04-01
The Vista disk should do it all for you.

---

### Post by Koolgecko91 on 2008-04-01
Thank you alot guys. Ubuntus been fun but my computer has trouble with it and im a student and I need to use certain Windows prgrams.

---

### Post by Calash on 2008-04-01
Well, Linux is not for everybody.  There are ways to continue working with it while maintaining a windows environment (Vitalization, dual booting) if you are interested in learning more.

In the end, function does win and if you need Windows, there is no reason not to use it.


Good luck :)

---

### Post by Koolgecko91 on 2008-04-01
Ive looked into them and i just dont think my comp can run them. And thanks again for the help.

---

### Post by forrestcupp on 2008-04-01
The Vista disk probably will *not* be able to format your disk.  It won't be able to see the ext3 partition.  Try [the GParted LiveCD](http://gparted.sourceforge.net/livecd.php) to delete all of your partitions and use your entire disk space to create a new NTFS partition.  Then Vista will be able to see your drive and install.

You can use GParted on your Ubuntu LiveCD, but you'll have to unmount your hard drive.

---

### Post by Duck2006 on 2008-04-01
For formatting the live cd of gparted or parted magic is the way to go.

---

### Post by Calash on 2008-04-01
If you tell it to delete the partition it should work fine...unless it has issues with that type of partition (OSX journaled comes to mind, XP disk cannot repartition it.)

Try the Vista disk first, if it can do it you are golden.  If not, use the disk listed above.

---


---
title: "before installing"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-03-17
Before I go ahead and install ubuntu, what should i do in windows. i have run disk defragmenter, is there anything else i need to do, bearing in mind that i want to duel boot. Also, is 50GB enough space?

---

### Post by idn on 2007-03-17
there isnt anything else you need to do, just run the installer on the live CD, make sure you partition your hard disk correctly you dont wnant to delete you windows partition. 50GB space is more than enough for a linux install, the ubuntu base install is just over 2GB i believe. 

You might want to think about creating a partition just for your home directory and  allocate the majority of the space for that, then you can store all your files on there and all the system files on another partition.

---

### Post by raja on 2007-03-17
If you plan to resize windows and install linux, it is a good idea to defragment beforehand and also take a backup. I am not sure what you have the 50 GB for. But about 5-10 GB for root,1 GB for swap and as much place as you want for /home would be enough.

---

### Post by Kobalt on 2007-03-17
Making a separate /home partition is a very good idea. Here is a [link]("http://psychocats.net/ubuntu/partitioning") you might find usefull to plan your patitions

---

### Post by ajeffreys on 2007-03-17
I also have a 250GB external hardrive with FAT32 format, so could i use that as an extra /home partition? It already has about 100GB of media files, so would i be able to access them?

---

### Post by buuntuu! on 2007-03-17
be sure to defrag more than once, the default defrag prog of xp isn't all to tidy and often leaves stuff behind. try [JKdefrag,]("http://www.kessels.com/JkDefrag/"). ugly gui, but it's excellent!
other than that there isn't much to worry about, unless maybe you have an ATI graphics card, read a lot of posts reporting problems with the live cd. in that case use the alternate cd

have fun with ubuntu

EDIT i don't recommend an external hd for /home!
a seperate home is recommendable however, for if you reinstall, break your system... your /home folder won't be affected... makes life easier!

---

### Post by ajeffreys on 2007-03-17
thankyou, i will try that program now :)

---

### Post by dstew on 2007-03-17
You can only have one partition mounted at /home, but you can always mount a partition from the big FAT drive to another mount point...

---

### Post by ajeffreys on 2007-03-17
I will try that then. is it easy to mount something like that though?

---

### Post by AtrejuT on 2007-03-17
mounting like that is quite easy. If you look around the forums you'll find plenty of detailed explanations. If you have your external HD permanently attached you could include it in the file /etc/fstab so thats what you have to look for.

You could e.g. mount your external HD in your homefolder in a folder /home/username/external if you want that. By default it should be mounted automatically to /media/usbdisk or so. 

atreju

---


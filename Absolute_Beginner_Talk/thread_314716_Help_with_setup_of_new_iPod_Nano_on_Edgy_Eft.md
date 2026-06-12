---
title: "Help with setup of new iPod Nano on Edgy Eft"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Jonathan Caprell on 2006-12-08
I recently bought my sister an iPod Nano for her birthday, and I'm having a bit of trouble setting it up.

I followed the guide at [http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071) down to the point where I've installed gtkpod and have selected "Read iTunesDB." From this point, however, I receive the error message

```
'/mnt/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.


```

I (thought that I) knew well enough to change the mount point to "/mnt/ipod" under the program's preferences, but that doesn't change anything that seems to be to my advantage in any way. The "File > Create iPod's Directories" option created the folders in the file structure, but I'm still lacking an iTunesDB, apparently. 

All in all, I'm pretty drained. Some help would be *greatly* appreciated.

---

### Post by quarkhirad on 2006-12-08
dear jonathan 

I dont use gtkpod for sync my 30 'Gb vedio ipod on linux. I use yamipod.
you can view the site [www.yamipod.com](www.yamipod.com) to see if ur ipod is supported or not.
If it is then try the following 
You can download the latest version of it from the site given below. Its a tar ball file just untar it and u will get 3 files 
1) a Readme 
2) a libfmodex file 
3) yamipod executable.

Just connect your ipod and make sure its mounted. 

then double click on the yamipod executable file.
 
It will give you a warning that file libfmod(Thats file no 2 in the list ) is not in a certain directory.

Just open the terminal and copy the libfmodex file to the directory that was stated in the warning. 

Note : usually the directory is /usr/lib. But dont take it as a default i have seen systems ask for it in other directories.

Restart yamipod by double clicking on the yamipod icon and it should automatically detect ur ipod.


[http://www.yamipod.com/main/modules/downloads/](http://www.yamipod.com/main/modules/downloads/)

All the best 

Cheers

---

### Post by daz4126 on 2006-12-09
Use Banshee, I found it works really well with my nano.

DAZ

---

### Post by dmjones500 on 2006-12-12
Hi,

I had problems with using a new iPod Nano with 6.10.  I found that installing the latest gtkpod and libgpod did the trick.  Unfortunately, they were only released a few weeks ago, and require compiling from source, and the slightly messy removal of previously installed packages.

See my thread here: [http://ubuntuforums.org/showthread.php?t=316244](http://ubuntuforums.org/showthread.php?t=316244) for a HOWTO.

---

### Post by Jonathan Caprell on 2006-12-25
Hey, I'm sorry to bump such an old topic, but I just wanted to let you know that I gave up on my sister's and just formatted it using one of my high school's Windows PC's. However, I've got my own iPod now, and I wanted to know if there were some way to format it on Ubuntu without using iTunes on Windows to do it first. Anyone able to help?

---

### Post by blakesmith on 2006-12-25
I just used gtkpod to format mine.  All I did was place a song in the iPod playlist and hit Sync, minutes later I had a fully functional iPod.

---


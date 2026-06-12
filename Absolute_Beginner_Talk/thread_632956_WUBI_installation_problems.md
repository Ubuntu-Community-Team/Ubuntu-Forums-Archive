---
title: "WUBI installation problems"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by zerofreeze on 2007-12-06
i installed wubi and chose the size for linux to be"4GB" and now whenever i install a program it tells me "there's no space on destination". can i enlarge the space again ?

---

### Post by overdrank on 2007-12-06
> **zerofreeze said:**
> i installed wubi and chose the size for linux to be"4GB" and now whenever i install a program it tells me "there's no space on destination". can i enlarge the space again ?
Hi and I do not think you can resize wubi because it is not like a partition, but a file contained within windows and it tricks windows into thinking that it is a separate drive. This is according to the FAQ on wubi site. You may search here for you answer and future questions. Good luck! 
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by Joeb454 on 2007-12-06
You'll need a bigger drive, if I remember rightly a normal install will take up around 4GB on your drive...which is still a lot smaller than Vista's 15GB lol

---

### Post by mpince on 2007-12-07
I did the same thing-- installed wubi with only the 4GB option.

---

### Post by mpince on 2007-12-10
[COLOR="Blue"][SIZE="4"]WAIT!!! There is a way.[/SIZE]

It is posible to create a new larger "home" vitual disk and copy your old home files there. I just enlarged my home directory to 10 GB. I found this guide somewhere and it works. Much easier than reinstalling wubi/ubuntu.[/COLOR]

------------------

Create and format a new virtual disk file (note that these instructions were for Wubi 7.04, I can't remember the specific pathnames for Wubi 7.10 at the moment but the general approach is the same): 


```
cd /media/host/wubi/disks
sudo dd if=/dev/zero of=extra.virtual.disk bs=1000 count=0 seek=$[1000*1000*10]
sudo mkfs.ext3 -F extra.virtual.disk
```

In this example, the file generated is 10 GB, change the numbers at the end of the command beginning with dd to adjust the sizes.

Now, once you have a virtual disk file, you mount it:

```
sudo mkdir /media/newhome
sudo mount -o loop extra.virtual.disk /media/newhome
```

Then you recursively copy the contents of /home to /media/newhome:

```
sudo rsync -avx /home/ /media/newhome
```
Now unmount the new virtual disk and remove the mountpoint:
```
sudo umount /media/newhome
sudo rm -r /media/newhome
```

Now reboot into Windows and move [COLOR="DarkSlateGray"]C:\wubi\disks\home.virtual.disk[/COLOR] somewhere else and rename [COLOR="DarkSlateGray"]extra.virtual.disk[/COLOR] to [COLOR="DarkSlateGray"]home.virtual.disk[/COLOR], 

Then you should have a new /home with a larger size If you get errors about /media/host/wubi not existing, Perhaps try /media/host/ubuntu on the commands instead or navigate to /media and see which folder your windows partition's contents are mounted at (I can't recall off the top of my head which it was in Wubi 7.10)

---

### Post by dr_gauravsuneja on 2007-12-22
i have downlaoded wubi installer for ubuntu7.10 even and palce the ubuntu iso made from magic iso and renamed it to ubuntu-7.10-dektop-i386.iso stillit doesn't recongize the is amd wants to downalod dektop.iso from net what 2 do?:popcorn:

---


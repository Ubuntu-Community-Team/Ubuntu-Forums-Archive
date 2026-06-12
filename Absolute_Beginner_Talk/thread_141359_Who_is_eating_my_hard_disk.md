---
title: "Who is eating my hard disk ?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Moloko on 2006-03-08
Hi, I have a problem starting GNOME, I only can log in as root, there is a error message if I try to log in with my user:

**mkdtemp: private socket dir: No space left on device**

I umounted all the non system partition to see the availabe space on my hard disk:

[B]root@tekram:/# mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/sdb2 on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
root@tekram:/





root@tekram:~# df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sdb1              12G   12G     0 100% /    <<=========================== Here is the problem I suppose.
tmpfs                 253M     0  253M   0% /dev/shm
/dev/sdb2             6,5G  2,1G  4,1G  34% /home
root@tekram:~#



root@tekram:~# cd /
root@tekram:/# ls -Sl
total 156
drwxr-xr-x    2 root root 49152 2005-10-15 19:13 lost+found
-rw-r--r--    1 root root 27149 2005-11-29 21:44 HP-LaserJet_1100-hpijs.ppd
-rw-r--r--    1 root root 10451 2005-11-18 21:46 ATI_LICENSE.TXT
drwxr-xr-x  115 root root  8192 2006-03-08 11:53 etc
drwxr-xr-x    2 root root  4096 2006-02-24 19:43 bin
drwxr-xr-x    3 root root  4096 2006-02-18 16:49 boot
drwxr-xr-x    2 root root  4096 2005-10-15 19:16 debootstrap
drwxr-xr-x    4 root root  4096 2006-01-28 18:36 home
drwxr-xr-x    2 root root  4096 2005-10-15 19:14 initrd
drwxr-xr-x   17 root root  4096 2006-03-01 20:58 lib
drwxr-xr-x    9 root root  4096 2006-03-06 19:43 media
drwxr-xr-x    2 root root  4096 2005-11-10 19:02 mnt
drwxr-xr-x    5 root root  4096 2006-02-11 12:17 opt
drwxr-xr-x   24 root root  4096 2006-03-08 11:27 root
drwxr-xr-x    2 root root  4096 2006-02-11 11:41 sbin
drwxr-xr-x    2 root root  4096 2005-10-15 19:14 srv
drwxrwxrwt   11 root root  4096 2006-03-08 12:05 tmp
drwxr-xr-x   16 root root  4096 2006-03-05 10:45 usr
drwxr-xr-x   15 root root  4096 2006-02-04 13:24 var
lrwxrwxrwx    1 root root    29 2005-11-23 17:18 initrd.img -> boot/initrd.img-2.6.12-10-386
lrwxrwxrwx    1 root root    28 2005-10-15 19:16 initrd.img.old -> boot/initrd.img-2.6.12-9-386
lrwxrwxrwx    1 root root    26 2005-11-23 17:18 vmlinuz -> boot/vmlinuz-2.6.12-10-386
lrwxrwxrwx    1 root root    25 2005-10-15 19:16 vmlinuz.old -> boot/vmlinuz-2.6.12-9-386
lrwxrwxrwx    1 root root    11 2005-10-15 19:13 cdrom -> media/cdrom
drwxr-xr-x   15 root root     0 2006-03-08 10:57 dev
dr-xr-xr-x  133 root root     0 2006-03-08 10:56 proc
drwxr-xr-x   10 root root     0 2006-03-08 10:56 sys
root@tekram:/#[/B]

I can see that I'm out of space, but I don't know what is happening, perhaps some file/s are growing or something similar, because short time ago when I did the "df -h" the system reports 11.5 Gb of 12 Gb used and now ports 12 Gb of 12Gb (the full disk).
Any help is wellcome.

Thanks in advance

---

### Post by soonindallas on 2006-03-08
you don't have 156 items listed.

```
ls -a
```

will show your hidden files & folders.

---

### Post by Moloko on 2006-03-08
Thanks, this is the result:

[B]root@tekram:/# ls -laS
total 164
drwxr-xr-x    2 root root 49152 2005-10-15 19:13 lost+found
-rw-r--r--    1 root root 27149 2005-11-29 21:44 HP-LaserJet_1100-hpijs.ppd
-rw-r--r--    1 root root 10451 2005-11-18 21:46 ATI_LICENSE.TXT
drwxr-xr-x  115 root root  8192 2006-03-08 12:28 etc
drwxr-xr-x   22 root root  4096 2005-11-29 21:44 .
drwxr-xr-x   22 root root  4096 2005-11-29 21:44 ..
drwxr-xr-x    2 root root  4096 2006-02-24 19:43 bin
drwxr-xr-x    3 root root  4096 2006-02-18 16:49 boot
drwxr-xr-x    2 root root  4096 2005-10-15 19:16 debootstrap
drwxr-xr-x    4 root root  4096 2006-01-28 18:36 home
drwxr-xr-x    2 root root  4096 2005-10-15 19:14 initrd
drwxr-xr-x   17 root root  4096 2006-03-01 20:58 lib
drwxr-xr-x    9 root root  4096 2006-03-06 19:43 media
drwxr-xr-x    2 root root  4096 2005-11-10 19:02 mnt
drwxr-xr-x    5 root root  4096 2006-02-11 12:17 opt
drwxr-xr-x   25 root root  4096 2006-03-08 12:28 root
drwxr-xr-x    2 root root  4096 2006-02-11 11:41 sbin
drwxr-xr-x    2 root root  4096 2005-10-15 19:14 srv
drwxrwxrwt   11 root root  4096 2006-03-08 12:30 tmp
drwxr-xr-x   16 root root  4096 2006-03-05 10:45 usr
drwxr-xr-x   15 root root  4096 2006-02-04 13:24 var
lrwxrwxrwx    1 root root    29 2005-11-23 17:18 initrd.img -> boot/initrd.img-2 .6.12-10-386
lrwxrwxrwx    1 root root    28 2005-10-15 19:16 initrd.img.old -> boot/initrd.i mg-2.6.12-9-386
lrwxrwxrwx    1 root root    26 2005-11-23 17:18 vmlinuz -> boot/vmlinuz-2.6.12- 10-386
lrwxrwxrwx    1 root root    25 2005-10-15 19:16 vmlinuz.old -> boot/vmlinuz-2.6 .12-9-386
lrwxrwxrwx    1 root root    11 2005-10-15 19:13 cdrom -> media/cdrom
drwxr-xr-x   15 root root     0 2006-03-08 10:57 dev
dr-xr-xr-x  123 root root     0 2006-03-08 10:56 proc
drwxr-xr-x   10 root root     0 2006-03-08 10:56 sys
root@tekram:/#
[/B]

Where are the missing files?
If lost+found dir is empty, why is the biger directory ?

---

### Post by kaamos on 2006-03-08
This will get you a little space
```
sudo apt-get clean
```
and this should get you some info where all the space is going to:
```

cd /
sudo du -hc --max-depth=1
```
You can change folders and vary the max-depth to get further results.

---

### Post by BoyOfDestiny on 2006-03-08
try 

df -h

Makes it human readable (my output)

/dev/sda1              16G  3.9G   13G  25% /
varrun               1007M   88K 1007M   1% /var/run
varlock              1007M  4.0K 1007M   1% /var/lock
udev                 1007M  216K 1007M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
/dev/sda2              97G   59G   38G  62% /home
/dev/hdd1             234G  100G  134G  43% /home/*****/Archive
/dev/sdb1             115G   65G   50G  57% /home/*****/Music
/dev/hdc1             280G  192G   89G  69% /home/*****/Video
/home                  97G   59G   38G  62% /chroot/home
/tmp                   16G  3.9G   13G  25% /chroot/tmp
/dev                 1007M  216K 1007M   1% /chroot/dev
/media/cdrom0          16G  3.9G   13G  25% /chroot/media/cdrom0
/usr/share/fonts       16G  3.9G   13G  25% /chroot/usr/share/fonts

If you need even more specific, go for du -h

Hope you can solve your problem!

---

### Post by Moloko on 2006-03-08
[QUOTE=kaamos]
and this should get you some info where all the space is going to:
```

cd /
sudo du -hc --max-depth=1
```
You can change folders and vary the max-depth to get further results.[/QUOTE]

Thanks a lot, with this command I think that I catch the problem in /var/backup:

```
root@tekram:/# du -hc --max-depth=1
48K     ./lost+found
2,0G    ./home
32K     ./media
33M     ./etc
8,5G    ./var
115M    ./lib
2,3G    ./usr
4,0M    ./bin
15M     ./boot
2,9M    ./dev
4,0K    ./mnt
515M    ./proc
4,5M    ./root
7,7M    ./sbin
96K     ./tmp
0       ./sys
4,0K    ./srv
45M     ./opt
4,0K    ./initrd
4,0K    ./debootstrap
14G     .
14G     total
root@tekram:/#
```

I installed sbackup utility, in the options I used other big hard disk as target for my backups, but now I can see two full backups in /var/bakcup using more than 4 Gb of space :???:  

There is another two big files, 1.8 Gb each one, that perhaps I can delete, but I dont know if it is safe:

/var/log/Xorg.0.log.old
/var/log/gdm/:0.log.1

Thank to all for your help and your patience.
Regards.

---

### Post by kaamos on 2006-03-08
I'm sure the first one can be removed safely and the second one is probably the same. Before that, you should have a look in the log files to see what is causing that. There is probably some error message repeater over and over again.

Since the files are so huge, use "cat" or "more" or something similiar:
```
more /var/log/Xorg.0.log.old
```
This is how you can make the file empty and free the space:
```
sudo su
echo "" > /var/log/Xorg.0.log.old
exit
```

---

### Post by Moloko on 2006-03-08
[QUOTE=kaamos]I'm sure the first one can be removed safely and the second one is probably the same. Before that, you should have a look in the log files to see what is causing that. There is probably some error message repeater over and over again.

Since the files are so huge, use "cat" or "more" or something similiar:
```
more /var/log/Xorg.0.log.old
```
This is how you can make the file empty and free the space:
```
sudo su
echo "" > /var/log/Xorg.0.log.old
exit
```[/QUOTE]

The .old file was deleted for the system I think, because does not appear now.
As you said the other is reflecting the same problem all the time, I will look what is happening later, now that I have access again to the GNOME desktop :) 

```
marcos@tekram:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sdb1              12G  5,0G  5,9G  47% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/sdb2             6,5G  2,1G  4,1G  34% /home
/dev/hda1              49G   36G   14G  74% /home/marcos/wind
/dev/hda2             136G   48G   81G  37% /home/marcos/almacen
/dev/hdc1              20G   12G  8,4G  57% /home/marcos/fat32
/dev/sda1              19G  8,6G   11G  45% /home/marcos/winc
marcos@tekram:~$

```


Thanks again.

---

### Post by deBaas on 2006-03-08
Is also looks like you have two kernels installed. Why not delete the old one when the newer is working find?

---

### Post by Zeroangel on 2006-03-08
Open up Synaptic. Where all the packages are listed press on the 'size' column label to sort them by size.

Also, run this command```
sudo du | sort -n
``` and it will list the most space-consuming folders at the bottom. Find out there what is eating up space.

---

### Post by nekr0z on 2006-03-09
I've got yet another problem with my hard disk: I use an external USB HDD, 160 GB big (at least this is what is printed on the cover), formatted in ext3 (one and only primary partition sized as big as posible). The disk is mounted in system permanently (with the corresponding options in /etc/fstab).

The thing is, I right-click the directory, which is the mountpoint for this disk, see "properties" (maybe wrong translation, my system says it in Russian, but you all know what I mean):

Type: folder.
Contains: 21269 objects, with the total of **129.1 GB**
Volume: **149.1 GB** volume
Free space: **[COLOR="Red"]28.0 kB[/COLOR]**

I just wonder, WHERE THE HELL COULD 20 GB FREE SPACE GO???!!! I really miss those 20 gigs!

---

### Post by kaamos on 2006-03-09
Go to the drive with the file manager and press ctrl+h. This shows you hidden (starting with a dot) files and directories. There could be a folder called ".Trash" with a lot of stuff in it.

---

### Post by Jucato on 2006-03-09
Have you checked using the du command?
I'd also like to offer a GUI alternative, but I'm not sure how well it works in GNOME (it's a KDE app, I think). The app is called Filelight and it's found in the universe repositories.

It gives you a graphical representation of the occupied and free space of your storage devices and color codes separate sections for easier interpretation. You might want to give it a whirl if you're interested.

---

### Post by nekr0z on 2006-03-09
Well, there is a .Trash folder there, 7.4 GB big. Not 20 Gb anyway, but This helps too. I'm extremely surprised hidden folders do not count in that properties window, it doesn't seem logical...

Filelight (thanks for hint, Fenyx!) says I have 136 GiB in that folder. But still, 13 GB of space seems to be relocated to some parallel universe?

---

### Post by Moloko on 2006-03-10
[QUOTE=deBaas]Is also looks like you have two kernels installed. Why not delete the old one when the newer is working find?[/QUOTE]

Hi again, I suposse that you are talking about this two files:

lrwxrwxrwx 1 root root 28 2005-10-15 19:16 initrd.img.old -> boot/initrd.img-2.6.12-9-386
lrwxrwxrwx 1 root root 25 2005-10-15 19:16 vmlinuz.old -> boot/vmlinuz-2.6.12-9-386

GRUB shows this version of kernel as the second option to boot, if I really don't need this old kernel, can I remove this files without problems or perhaps is a way to have a "backup" kernel ?

I'm not confident working with kernels and try to be cautious.

Regards.

---

### Post by landotter on 2006-04-25
[quote=Fenyx]Have you checked using the du command?
I'd also like to offer a GUI alternative, but I'm not sure how well it works in GNOME (it's a KDE app, I think). The app is called Filelight and it's found in the universe repositories.

It gives you a graphical representation of the occupied and free space of your storage devices and color codes separate sections for easier interpretation. You might want to give it a whirl if you're interested.[/quote]

Baobab is a great Gnome app for checking disk usage.

---

### Post by Ares139 on 2006-04-25
Would [KDirStat]("http://kdirstat.sourceforge.net/") be of any help?  I'm not sure, I'm pretty new around here (first post even), but the [Windows version]("http://windirstat.sourceforge.net/") helped me with problems like this.

-Ares

---

### Post by auroraborealis on 2006-04-25
I'll second baobab. Actually I was going to suggest it but landotter beat me to it.

---


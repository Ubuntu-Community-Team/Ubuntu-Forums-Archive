---
title: "Installation problems"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by robstat on 2008-03-22
Hello there I am a newby so be gentle.

 I've tried to install 7.10 on my laptop at work with the intention of scraping ms but I can't get it to install. It's a hp g6065ea, amd 64 athlon x2, nvidia graphics. Firstly I tried the standard 7.10 now I've tried the 64 bit version, I've also tried a few entries eg. noapic and noapci. After the cd is run it it srolls alot of code the brings a dialogue box saying ubuntu is running in low graphics mode when continued it sticks on ubuntu@ubuntu: (wavey line dollar) (which I can't find on my keyboard) obviously waiting for input from me!
I can get the live cd on if it's in safe graphic mode but after I try to install the boxes are off the screen so I can't get to the buttons.
Thanks for looking and will be greatfull for any help. Rob

---

### Post by spiderbatdad on 2008-03-22
[http://ubuntuforums.org/archive/index.php/t-691147.html](http://ubuntuforums.org/archive/index.php/t-691147.html)

---

### Post by gsmanners on 2008-03-22
You probably need to do a low memory install.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by robstat on 2008-03-23
I'm downloading the iso at the moment so will give it a go tonight but can someone explain why a low memory install will help as I'm running 2gb ram please?

---

### Post by seshomaru samma on 2008-03-23
I don't think you need a low-memory install with 2GB
> I can get the live cd on if it's in safe graphic mode but after I try to install the boxes are off the screen so I can't get to the buttons with 2gb
you can hold alt and move the mouse -that will move the window so you can get to buttons

---

### Post by robstat on 2008-03-23
> **seshomaru samma said:**
> I don't think you need a low-memory install with 2GB

you can hold alt and move the mouse -that will move the window so you can get to buttons

No I've tried shrinking the windows and moving them but I can't get to the buttons:confused:
Would I have more chance with 8.04 beta?

---

### Post by jan quark on 2008-03-23
the easiest way to overcome graphical problems during the installation is to use the text mode installation and install all needed drivers after the successful installation

here the download site for the alternate CD:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

here a good guide for text based installation:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by spiderbatdad on 2008-03-23
Since this is your first Ubuntu install, I would recommend the 8.04 beta. You hp hardware is likely to have better support. Though do realize updates are very regular at this time, and the os is not stable.

---

### Post by robstat on 2008-03-23
> **spiderbatdad said:**
> Since this is your first Ubuntu install, I would recommend the 8.04 beta. You hp hardware is likely to have better support. Though do realize updates are very regular at this time, and the os is not stable.

I'll try 8.04 just to see if it installs

---

### Post by robstat on 2008-03-23
> **jan quark said:**
> the easiest way to overcome graphical problems during the installation is to use the text mode installation and install all needed drivers after the successful installation

here the download site for the alternate CD:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

here a good guide for text based installation:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

The link is hanging but I had this downloading earlier this morning but i closed my laptop before I went out and froze the download now I can't find it but I'll try 8.04 first then I'll try this if i get no joy.
Thanks to all for the advice so far. Rob

---

### Post by robstat on 2008-03-23
I've got 8.04 beta working no problem at all with the install, Many thanks to all that gave me advice:)
One small problem, I manually partitioned my hard drive and set a swap, ext3 and a 40gb partition formatted to fat32 so I could use it with windows and ubuntu, now I can see the partition with vista but not ubuntu. What did I do wrong and how do I put it right?

---

### Post by lswest on 2008-03-23
can you post the output of ```
sudo fdisk -l
``` from the terminal (applications-->accessories-->terminal)?  also, it's always best if you do 1 thread per problem/question

---

### Post by robstat on 2008-03-23
> **lswest said:**
> can you post the output of ```
sudo fdisk -l
``` from the terminal (applications-->accessories-->terminal)?  also, it's always best if you do 1 thread per problem/question

rob@rob-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ff16d35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10942    87891583+   7  HPFS/NTFS
/dev/sda2           17953       19457    12088912+   7  HPFS/NTFS
/dev/sda3           10943       16128    41656545    5  Extended
/dev/sda4           16129       17952    14651280   83  Linux
/dev/sda5           10943       15927    40041981    b  W95 FAT32
/dev/sda6           15928       16128     1614501   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oettinger on 2008-03-23
Just a tiny bit off topic, but the wavy key is a tilde, it is made by using <shift> and the key right above the tab key~~

---

### Post by robstat on 2008-03-23
> **oettinger said:**
> Just a tiny bit off topic, but the wavy key is a tilde, it is made by using <shift> and the key right above the tab key~~

Thanks but shift and the key above the tab key on my keyboard is ¬ oh i've just found it, it's above the right hand shift key~~~ Thanks anyway
Back to the topic I think while just looking for music files I think I've mounted my 40gb partition (by accident) it's now on my desktop:)

---

### Post by seshomaru samma on 2008-03-24
when you go to places>computer>file system>media do you see sda5?

---

### Post by robstat on 2008-03-24
No I can only see:
cdrom
cdrom0
sda1
sda2

---

### Post by seshomaru samma on 2008-03-25
> No I can only see:
cdrom
cdrom0
sda1
sda2
strange , i guess you will have to manually mount it
can you post your /etc/fstab
```
cat /etc/fstab
```

---

### Post by robstat on 2008-03-26
I'll try to do it tomorrow if I can remember the laptop is at work and no internet. Thanks

---

### Post by robstat on 2008-03-27
rob@rob-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=9414124a-44ad-4d7d-aa91-1aae11272d96 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=5CD72D6708700F3A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=4CF6-52ED  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=b9c97092-2ed7-4614-adbc-627ac4480a94 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
rob@rob-laptop:~$ 

I hope you can see what this is I can't make head nor tail of it:)

---

### Post by seshomaru samma on 2008-03-30
according to the fstab you should be able to see your FAT32 partition as a folder called "windows"
do you see it in places>computer>file system?

---

### Post by robstat on 2008-04-01
All sorted now many thanks I clicked on it in places and it appeared on my desktop:) It will be a lot easier when I learn my way around.Thanks again Robstat

---


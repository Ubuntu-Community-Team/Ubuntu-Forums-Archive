---
title: "Sudo, Permission, giFT"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by take_one on 2006-04-06
Hello,

I read a lot in this community that su doesn't work in kubuntu, only sudo works, but why su works on mine? 

Me myself is a new comer. My Kubuntu was installed by my ex-boyfriend. Since i don't have him anymore, i sort have to get along with this OS :???:. So guys if you ask me what kubuntu i have exactly? i don't know :oops: But i know that i fixed some easy problems like installing missing component for K3B, JRE for Konqueror and Firefox, created root password and all were done in the console \\:D/ 

However, i have more problems :confused: 

1. I can't save files into my other partition. My PC was partitioned into 3. One for windows, one for linux and one for "share". I had debian before my windows went death just like that (we reinstalled both OS again) and i could "read and write" files from debian in the 3rd partition. Now i can't. I did realise that the file permission wasn't rwxr-xr-x then i changed it, but i still can't save stuffs (but can read tho). Can somebody help me?

2. I posted this problem a couple of times already, but got no responses :roll:. I got this alert last time: "Sorry, I couldn't locate your giFT installation,please select the path to your giFT like /.../share/giFT". I found gift file under: /usr/share/doc/gift, so i created this path in Apollon and the alert went. However, it won't connect. Do you know why?

I have always been interested on this OS. I like the idea and the philosophy behind it and after visiting an OS lecture last semester i learned how powerfull open-source OS like this. It's just that i've been too lazy to configure and fixing. Why wouldn't i just shout out laud and complain while i have someone, who would configure and fix it for me? Well i guess i learned my lesson. There's always a bright side from a bad luck :mrgreen:

So are you going to help me? please? [-o< ;)

---

### Post by aysiu on 2006-04-06
Is your shared partition FAT32?

---

### Post by take_one on 2006-04-06
Yes i think so...

---

### Post by aysiu on 2006-04-06
Can you go to a terminal and post here the output of these three commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
``` Gnome: Applications > Accessories > Terminal
KDE: KMenu > System > Konsole

---

### Post by take_one on 2006-04-06
sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30473    15358108+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           30474       54044    11879784   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           54045      116296    31374945    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/hda5           54045       54857      409626   82  Linux swap / Solaris
/dev/hda6           54857      116296    30965256    b  W95 FAT32

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              12G  2.8G  7.9G  26% /
tmpfs                 110M     0  110M   0% /dev/shm
/dev/hda1              15G  7.5G  7.2G  52% /media/hda1
/dev/hda6              30G   25G  5.4G  82% /media/hda6

---

### Post by aysiu on 2006-04-06
Try this: ```
sudo mkdir /shared
sudo umount /dev/hda6
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace this line ```
/dev/hda6 /media/hda6 vfat defaults 0 0
``` with this ```
/dev/hda6 /shared vfat iocharset=utf8,umask=000 0 0
``` Save (control-x), confirm (y), and exit (Enter). ```
sudo mount -a
```

---

### Post by take_one on 2006-04-06
i got this for the second code, then i stoped. Should i continue?

root@tika:/home/tika# umount /dev/hda6
umount: /media/hda6: device is busy
umount: /media/hda6: device is busy

---

### Post by ubuntuuser on 2006-04-06
You could also just reboot, then you won't get these messages. I had some problems with the iocharset=utf8 parameter. Got some strange error messages, so I simply deleted this part in my fstab. Works like a charm.

---

### Post by aysiu on 2006-04-06
[QUOTE=take_one]i got this for the second code, then i stoped. Should i continue?

root@tika:/home/tika# umount /dev/hda6
umount: /media/hda6: device is busy
umount: /media/hda6: device is busy[/QUOTE] I don't know if this makes a difference, but you know you're using a root terminal instead of a regular terminal with *sudo*? If the device is "busy," just forget about the umount command for now. Do the rest of the steps and reboot instead of doing *sudo mount -a* at the end.

---

### Post by take_one on 2006-04-06
i know why it was busy. I was listening music saved in that partition. I stopped it and continued your instruction. Now my hda6 is empty :(

---

### Post by aysiu on 2006-04-06
[QUOTE=take_one]i know why it was busy. I was listening music saved in that partition. I stopped it and continued your instruction. Now my hda6 is empty :([/QUOTE] What do you mean by it's "empty"? You rebooted after changing the /etc/fstab, right? Have you looked in the folder called /shared?

---

### Post by take_one on 2006-04-06
Oh i got it... it works yeeeaaaa.... it's under shared right!! THANKS!!

---

### Post by take_one on 2006-04-06
Hello aysiu,

Thanks a lot. Great job. I learned more. I understood what you were trying to say with the codes. Linux rocks :mrgreen:

Tika

---

### Post by aysiu on 2006-04-06
Glad it all worked out for you.

---

### Post by take_one on 2006-04-07
Hey guys, i got my partition works wonderful now from a help of someone claimed himself to be an amature :rolleyes: 

This comunity is nice... people stay down to earth all the time :mrgreen: 

I still wonder tho, about su. Can anyone tell me, why su works on mine, while it read that only sudo works for kubuntu. Also i used 
sudo -s //to go to root and 
passwd //to set my password

did i do it right?

---

### Post by ubuntuuser on 2006-04-07
[QUOTE=take_one]
I still wonder tho, about su. Can anyone tell me, why su works on mine, while it read that only sudo works for kubuntu. Also i used 
sudo -s //to go to root and 
passwd //to set my password

did i do it right?[/QUOTE]
As far as I know, su is a part of most linux distributions and should work for everyone working with (k)ubuntu. And yes, you did it right, BUT:

Keep in mind that, if you use sudo -s, you become root for the whole time until you type exit or close the terminal window. Be careful when running as root! Be sure to logout of the root account as soon as you are done. Running as root is dangerous, and should only be used when needed. Typos or mistakes can destroy your system or your data, so it is important that you be careful when running as root. This may sound dramatic, but keep that in mind. A safer way to accomplish what you want is to use ```
sudo passwd root
```because you will only run "passwd root" as root and then automatically become a regular user again.

---

### Post by take_one on 2006-04-07
Hey, thanks for the tips... i will keep it in mind about not running as root too much...

---


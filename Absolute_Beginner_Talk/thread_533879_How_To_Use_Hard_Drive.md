---
title: "How To Use Hard Drive"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-08-24
i am using ubuntu and windows xp , as i cant write ntfs drives of xp on linux so i converter two of my drives to ext3 fomat . now how to paste my data from home folder to these 2 drives?

---

### Post by damansandhu on 2007-08-24
somebody plz answer

---

### Post by punx45 on 2007-08-24
if the drives are already mounted, then a simple cp will work.

cp /home/whatever /mount/point/of/drive    (these are not literal paths of course :) )

---

### Post by damansandhu on 2007-08-24
it says cannot mount volume

---

### Post by loserboy on 2007-08-24
you could also install ntfs-3g and write to the windows drives

---

### Post by loserboy on 2007-08-24
when you made those new partitions did you give them a mount point?

---

### Post by damansandhu on 2007-08-24
ok , but my two ext3 drives are showing but i cannot paste any data in them

---

### Post by damansandhu on 2007-08-24
help plzz

---

### Post by anubhavrocks on 2007-08-24
Click on the Panel ->Add to panel->Disk Mounter
use this applet to mount the drives

---

### Post by damansandhu on 2007-08-24
you didn't get my point , i see 7 drives on my computer , 1 is filesystem of linux , 2 are ext3 drives and remaining 4 are ntfs drives in which my windows games and applications are kept . the thing is i want to use the two ext drives like i like other four drives in windows .
so i dont know how to do that

---

### Post by schorsch on 2007-08-24
What is the output of
```
sudo fdisk -l
```
... it is a lowercase "L" at the end ...

---

### Post by damansandhu on 2007-08-24
ok when i right click on one of those ext3 drives and then select properties , then permissions then access , default is read-only , when i try to change it to read and write ,it says the permissions could not be changed.

---

### Post by damansandhu on 2007-08-24
daman@Ultimate:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       19457   136753312+   f  W95 Ext'd (LBA)
/dev/sda5            2433        3612     9478318+  83  Linux
/dev/sda6            3613        4864    10056658+  83  Linux
/dev/sda7            4865        7296    19535008+   7  HPFS/NTFS
/dev/sda8            7297        8476     9478318+  83  Linux
/dev/sda9            8477        9541     8554581   83  Linux
/dev/sda10           9542        9728     1502046   82  Linux swap / Solaris
/dev/sda11           9729       14592    39070048+   7  HPFS/NTFS
/dev/sda12          14593       19457    39078081    7  HPFS/NTFS
daman@Ultimate:~$

---

### Post by schorsch on 2007-08-24
... and add the output of 
```
mount
```
as your devices seem to be mounted already

---

### Post by damansandhu on 2007-08-24
daman@Ultimate:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda9 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda11 on /media/sda11 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda12 on /media/sda12 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda7 on /media/sda7 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=daman)
/dev/sda5 on /media/DAMAN_ type ext3 (rw,nosuid,nodev)
/dev/sda8 on /media/DAMAN type ext3 (rw,nosuid,nodev)
daman@Ultimate:~$

---

### Post by schorsch on 2007-08-24
I guess the partitions in question are /dev/sda5 and /dev/sda8, right? Please post the output of 
```
ls -ld media/DAM* 
whoami
id
```

---

### Post by damansandhu on 2007-08-24
daman@Ultimate:~$ ls -ld media/DAM*
ls: media/DAM*: No such file or directory
daman@Ultimate:~$ whoami
daman
daman@Ultimate:~$ id
uid=1000(daman) gid=1000(daman) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),118(admin),1000(daman)
daman@Ultimate:~$

---

### Post by anubhavrocks on 2007-08-24
try ext2fs

---

### Post by damansandhu on 2007-08-24
i know which are my ext3 drives , i just want to paste some data in them which i cant

---

### Post by anubhavrocks on 2007-08-24
try Explore2fs

---

### Post by schorsch on 2007-08-24
Uhm sorry, there was a typo inside:
```
ls -ld /media/DAM* 
```

---

### Post by damansandhu on 2007-08-24
i can see my 2 drives , i can even access the files present in them , i can copy anything from these 2 drives , the thing is i cannot write or paste anything in these drives.

---

### Post by damansandhu on 2007-08-24
daman@Ultimate:~$ ls -ld /media/DAM*
drwxr-xr-x 3 root root 4096 2007-08-24 23:37 /media/DAMAN
drwxr-xr-x 3 root root 4096 2007-08-24 23:36 /media/DAMAN_
daman@Ultimate:~$ whoami
daman
daman@Ultimate:~$ id
uid=1000(daman) gid=1000(daman) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),118(admin),1000(daman)
daman@Ultimate:~$

---

### Post by schorsch on 2007-08-24
```
sudo chown daman:daman /media/DAM*
```
So you will be able to write to both devices at the top level directory. If you need to change the permissions on some subdirectories too you should type
```
sudo chown -R daman:daman /media/DAM*
```
Be warned: Changing permissions recursively (with the parameter "-R") can cause trouble sometimes !!!!

---

### Post by damansandhu on 2007-08-24
thanks for the help , how to change names of these 2 drives?

---

### Post by schorsch on 2007-08-24
From your last reply I guess you could write now, right? Regarding your question about the names of these 2 drives: 
a) With "names" you think of "/media/DAMAN*" ?
b) Do you want them to be mounted automatically after an reboot?
c) Which "name" do you want?

---

### Post by damansandhu on 2007-08-24
i want to rename "DAMAN: DAMAN (3)" to "DAMAN: HDD1" AND "DAMAN (2): DAMAN (4)" TO "DAMAN: HDD2"

---

### Post by schorsch on 2007-08-24
Sorry, I do not understand the answer.
Right at the moment the devices are mounted to "/media/DAMAN" and "/media/DAMAN_". Do you want them to be mounted to "/media/DAMAN_HDD1" and "/media/DAMAN_HDD2"? I suggest these names as a colon in the name of a directory can cause trouble sometimes? And also after a reboot?

---

### Post by damansandhu on 2007-08-24
OK , I THINK I SHOULD LEAVE IT , thanks for you help.

---

### Post by schorsch on 2007-08-24
I'd guess if you reboot these devices will not be mounted automatically .. do you want them to be mounted after a boot?

---

### Post by damansandhu on 2007-08-24
yea , i want them to be mounted automatically after reboot

---

### Post by schorsch on 2007-08-24
Well, first create the directories that you want to mount the devices to. I will use my proposed "names" in this guide.
```
sudo mkdir /media/DAMAN_HDD1
sudo mkdir /media/DAMAN_HDD2
```
Then you have to edit the file /etc/fstab:
```
gksudo gedit /etc/fstab
```
Add the following lines at the end:
```
/dev/sda8  /media/DAMAN_HDD1  ext3  defaults 0 1
/dev/sda5  /media/DAMAN_HDD2  ext3  defaults 0 1
```
To test if it works you should type:
```
sudo umount /dev/sda8
sudo umount /dev/sda5
sudo mount -a
```
Of course you can change the proposed "names" as you like. But everything should be done now.

---

### Post by damansandhu on 2007-08-24
thanks for your help man

---

### Post by schorsch on 2007-08-24
Glad to hear that it seems to work now! Could you please mark this thread as solved as this can help others, too?

---


---
title: "mounting xp in ubuntu"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by snobby500 on 2007-07-02
Hey, i was able to acess all my files in xp untill coulpe of days ago, i think it was caused by us backing up my windows partition with a program called acromis 10, and saving the file in ubuntu, under filesystem (not in any of the folders) but just in filesystem, i tried deleting it but that didnt help, all my music is on there, so if anyone has any ideas, plz let me know :)

thanks

---

### Post by Beaucephus on 2007-07-02
Is the XP filesystem mounted?

Try
```
cat /etc/mtab
```
in a terminal and you should see an NTFS or VFAT filesystem.

If it is not there try
```
mount -t NTFS /dev/### /media/mountdirectory
```
where "###" is the drive and "mountdirectory" is the mount point (you may have to create it).

---

### Post by snobby500 on 2007-07-02
this is what i got:

alex@alex:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
alex@alex:~$ mount -t NTFS /dev/xp /media/1
mount: only root can do that
alex@alex:~$ sudo mount -t NTFS /dev/xp /media/1
Password:
mount: mount point /media/1 does not exist
alex@alex:~$ sudo mount -t NTFS /dev/xp /media/0
mount: mount point /media/0 does not exist
alex@alex:~$ sudo mount -t NTFS /dev/xp /media/2
mount: mount point /media/2 does not exist
alex@alex:~$ sudo mount -t NTFS /dev/xp /media/3
mount: mount point /media/3 does not exist
alex@alex:~$ sudo mount -t NTFS /dev/xp /media/xp
mount: unknown filesystem type 'NTFS'
alex@alex:~$ sudo mount -t NTFS /dev/xp /media/xp
mount: unknown filesystem type 'NTFS'
alex@alex:~$ 

the bottom line is done twice :)

by the way i have a folder in media called xp, took me a sec to remember, and thts where all my old files and stuff used to be, and now its just blank. 

does this make any sense? the thing i dont get is it was working absoultely great before :S

i have another xp installed on a virtual machine, using virtualbox, this wouldnt make any difference right?

---

### Post by davidjmayo on 2007-07-02
To mount your XP partition first do

```
sudo fdisk -l
```

See the one which says NTFS 

The NTFS partition is  /dev/hda? (? is the number for your NTFS partition)

Now you can mount the partition

```
mount -t NTFS /dev/hda? /media/XP
```

change ? to the number you got from fdisk -l 

Now it should be mounted. Check with


```
cat /etc/mtab
```

and you should see it

> by the way i have a folder in media called xp, took me a sec to remember, and thts where all my old files and stuff used to be, and now its just blank.

does this make any sense? the thing i dont get is it was working absoultely great before :S


yes it makes sense

---

### Post by snobby500 on 2007-07-02
thanks for all the replies, it turned out to be something really simple:
i hadnt shut down wnidows properly last time so it still had the hard drive mounted, therefore ubuntu couldnt mount it (or thats what i understood :))
thanks again for all the help

---

### Post by Beaucephus on 2007-07-02
Snooby I thought I might explain that "empty directory" thing.  

When you mount a hard drive you are telling your machine *where* to mount it and this is a directory.  

For instance your XP files are at mounted at /media/xp.  The files are not actually located there, but this directory points towards the device where the files are located.  If the hard drive is NOT mounted /media/xp will appear as an empty directory.  

Ubuntu is so easy to use that it is possible to glaze over Linux fundamentals.  I recommend everyone read "Running Linux" published by Oreily.

---

### Post by snobby500 on 2007-07-06
thanks, it makes sense now :)

---


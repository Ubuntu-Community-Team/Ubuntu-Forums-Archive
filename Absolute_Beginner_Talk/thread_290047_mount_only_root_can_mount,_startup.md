---
title: "mount: only root can mount, startup"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by scotty76uk on 2006-10-31
Hi Im a newbie just install ubuntu for first time and have been trying to mount my FAT32 spare drive which has my music and docs on it so i can share with Linux. I managed to mount the drive fine and access files no problem. But when I restarted I have to remount again. Looking through the forums and online I found I have to edit  fstab. I used the following code

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

then added the following line to the end of the fstab file

/dev/hda1   /media/windows  vfat  iocharset+utf8,unmask=000 0  0

I saved this and then rebooted

After rebooting when i clicked on the drive to access it i got the following message 

"mount: only root can mount /dev/hda1....."

I looked with in SYSTEM - ADMINISTRATION - DISCS

and can see that the drive has been save to the correct directory but i still get that message 

any ideas please?:-k

---

### Post by taurus on 2006-10-31
Oops.  It should be "umask" not "unmask"...  ;)

---

### Post by Bachstelze on 2006-10-31
Hi and welcome to Ubuntu :)

First, are you sure your partition is /dev/hda1 ?

Second, it's umask, not u**n**mask.

Third, add 'user' to the mount parameters so you can mount it without being root.

---

### Post by scotty76uk on 2006-10-31
opps typo.. but yeah thats what i put into the terminal

---

### Post by scotty76uk on 2006-10-31
hi yes to the first two, windows is installed in SCSI 0 and Ubuntu to SCSI 1 spare drive is first primary ide drive

how do i "add 'user' to the mount parameters so you can mount it without being root."

Thanks!!! scott

---

### Post by taurus on 2006-10-31
What does the whole /etc/fstab look then?

```
more /etc/fstab
```

---

### Post by scotty76uk on 2006-10-31
I had to reboot into unbuntu i have a wireless LAN and havent got far enough to use ndiswrapper yet

ok this is the complete fstab file

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/music    vfat    iocharset=utf8,unmask=000       0
0
/dev/hdb1       /media/movies   vfat    iocharset=utf8,unmask=000       0
0


firstly yes I have two drives to be mounted, one music and one movies, and have made the appropriate ditectories, this was fine before i edited fstab

thanks

---

### Post by taurus on 2006-10-31
You need to remove the n in unmask since it should be **[SIZE="5"]umask[/SIZE]**, not unmask...

---

### Post by scotty76uk on 2006-10-31
doh ](*,)  yes that was the obvious mistake my bad, i wont be doing that again and atleast I know what the command does now

Thank you for your help

my next problem is ndiswrapper, but i suppose i need to post a new thread for that

thanks again!!

---

### Post by Sef on 2006-10-31
> my next problem is ndiswrapper, but i suppose i need to post a new thread for that


Yes, please start a new thread with an appropriate title.

---


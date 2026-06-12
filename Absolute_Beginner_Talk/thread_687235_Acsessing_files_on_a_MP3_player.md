---
title: "Acsessing files on a MP3 player"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-02-04
I have a few files on my Samsung yp-k3 that i would like to get off, how would i go about doing this?

---

### Post by LostMagix on 2008-02-04
I should have clarified, i would like it to act like a flash drive, so it just pops up on my desktop.

---

### Post by oedha on 2008-02-04
does it have usb cable ?
mostly gadget with usb cable will be automatically detected and displayed

you can work on it after that.......
if you used other Gutsy....you will have to delete the files by using shift+del

regards;
~E~

---

### Post by SpiderGorilla on 2008-02-04
What happens when you plug it in via USB?

---

### Post by LostMagix on 2008-02-04
When i plug in the USB it starts charging and i can add/remove music file via banshee music player, or like programs, but i cant figure out how to get the other files i have stored on it off.

---

### Post by LostMagix on 2008-02-04
I am hoping to be ably to use a file browser with it.

---

### Post by SpiderGorilla on 2008-02-04
If you go to Places, what do you see after Computer and CD/DVD Creator?

---

### Post by LostMagix on 2008-02-04
It does recognize it..

```
:~$ lsusb
Bus 004 Device 004: ID 04e8:5081 Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 19ff:0201  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000  
chris@LostMagix:~$ 

```

---

### Post by LostMagix on 2008-02-04
Nothing, a divider then network

---

### Post by SpiderGorilla on 2008-02-04
Okay. If you open up a browser window, on the left side do you see:

yourUserName
Desktop
File System
MP3PlayerName

At all?

---

### Post by LostMagix on 2008-02-04
Nope, only if i go into a media player do it see it

---

### Post by SpiderGorilla on 2008-02-04
Well, having looked over your MP3 player's specs, I'm not even sure if it supports that functionality. Uh, did you originally use this with Ubuntu or something else?

---

### Post by LostMagix on 2008-02-04
This is the first time i have ever tried to use it for anything else other then media on Linux yes

---

### Post by kpkeerthi on 2008-02-04
It should have been mounted as /media/sdx?

---

### Post by kpkeerthi on 2008-02-04
Open nautilus and look in /media. It should be there for sure. And you should be able to drag&drop files to it.

---

### Post by LostMagix on 2008-02-04
Whats nautilus?

I ran it in the terminal and it opened my home folder.

---

### Post by kpkeerthi on 2008-02-04
It is a file manager. Use it to navigate to /media folder. Your player should be mounted there (hopefully!).

---

### Post by LostMagix on 2008-02-04
nautilus /media = cdrom, cdrom0

---

### Post by kpkeerthi on 2008-02-04
What does **mount** output?
Run ```
mount
``` in a terminal and post back the output.

---

### Post by LostMagix on 2008-02-04
```
:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

---

### Post by kpkeerthi on 2008-02-04
I do not see your player listed there. Is it plugged in? 
Plug it in and when it is ready, post the output of **mount** and **sudo fdisk -l**

---

### Post by LostMagix on 2008-02-04
Its plugged in and accepting media file from rhythmbox....

```
:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

``` 


```
:~$ sudo fdisk -l

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd402

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4678    37576003+  83  Linux
/dev/sdb2            4679        4865     1502077+   5  Extended
/dev/sdb5            4679        4865     1502046   82  Linux swap / Solaris

```

---

### Post by kpkeerthi on 2008-02-04
> 
Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table


This appears to be your player. Is it a 4 GB player?

---

### Post by LostMagix on 2008-02-04
No its a 2gb, that my back up drive.


Nothing on it right now, it kinda defeats the purpose of having it.

---

### Post by oedha on 2008-02-04
how bout :==> sudo mount -a
question : have you turn on the boxes in the
system - preferences removable drives and media preferences ?

---

### Post by kpkeerthi on 2008-02-04
> how bout :==> sudo mount -a
That would remount the entries from fstab which I see no reason to run here.

---

### Post by LostMagix on 2008-02-04
I dont know what you mean, so im gonna say no the the boxxes

---

### Post by kpkeerthi on 2008-02-04
@LostMagix
fdisk does not seem to find it (fdisk -l). It is neither in the list of mounted filesystem (mount). I'm out of options. Sorry mate.

---

### Post by kpkeerthi on 2008-02-04
> I dont know what you mean, so im gonna say no the the boxxes
Yeah. Just one more try. Uncheck the automount option. Plug out the drive and plug it in back. Post the output of **sudo fdisk -l**.

---

### Post by LostMagix on 2008-02-04
oo i see what your saying, yes i have

---

### Post by LostMagix on 2008-02-04
```
:~$ sudo fdisk -l

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd402

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4678    37576003+  83  Linux
/dev/sdb2            4679        4865     1502077+   5  Extended
/dev/sdb5            4679        4865     1502046   82  Linux swap / Solaris

```

---

### Post by oedha on 2008-02-04
> **LostMagix said:**
> I dont know what you mean, so im gonna say no the the boxxes
no...mark them....
then...can you unplug it...then plug it again.....
because previously you said that you can use banshee right ?
(maybe...i am silly....)

---

### Post by kpkeerthi on 2008-02-04
I still can't find it listed. I'll leave this to someone more experienced. 
(I'm still puzzled why fdisk -l won't list your player)

---

### Post by LostMagix on 2008-02-04
K i just found out it will only mount in a media player if its set to that player in removable drives

---

### Post by kpkeerthi on 2008-02-04
So are you able to see it by running sudo fdisk -l now?

---

### Post by kpkeerthi on 2008-02-04
If fdisk can get it, I can help you mount it as a normal folder where you could copy just about anything to it.

---

### Post by LostMagix on 2008-02-04
Nope it still doesnt see it in sudo fdisk -l, yet it sees it in a media player.......



Ubuntu would be all i ever used if it wasnt for the hardware bullsh!t

---

### Post by LostMagix on 2008-02-05
Bump

---

### Post by LostMagix on 2008-02-18
why does it seem like i alway get the unsolvables.

---


---
title: "File permitions?????"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-03-28
Hi. I'm completly new to all administration what so ever. I have some abilities in computing but they are thinly spread. My question concerns accessing a windows partition to save and read data (to and from). System config

hda1  is 702MB HP loader or something ???
hda2  is 34GB Windows I wish to access

hdb1 is my  swap 1GB
hdb2 is my Ubuntu 4GB

now when i open nautilus (file browser) using "sudo" for root priviledges it still doesn't let me change the priviledges in the properties. while I can't access the hda1 or hda2 folders from the terminal using "sudo cd /media/hda1", I don't know how to exactly use the "chmod" command and what the synthax is (I already tried the man pages).

when I try to change the priviledges it gives an error saying I don't have premission even though I used sudo to start nautilus and that it is read only.

Why??

is it because I open properties in a dialog box that is the child of the sudo generated window or what? why can't I use sudo with cd? and what is the difference between gksudo and sudo?

Completly stumpt. Please help!!!!

---

### Post by Princey on 2006-03-28
[QUOTE=belikralj]Hi. I'm completly new to all administration what so ever. I have some abilities in computing but they are thinly spread. My question concerns accessing a windows partition to save and read data (to and from). System config

hda1  is 702MB HP loader or something ???
hda2  is 34GB Windows I wish to access

hdb1 is my  swap 1GB
hdb2 is my Ubuntu 4GB

now when i open nautilus (file browser) using "sudo" for root priviledges it still doesn't let me change the priviledges in the properties. while I can't access the hda1 or hda2 folders from the terminal using "sudo cd /media/hda1", I don't know how to exactly use the "chmod" command and what the synthax is (I already tried the man pages).

when I try to change the priviledges it gives an error saying I don't have premission even though I used sudo to start nautilus and that it is read only.

Why??

is it because I open properties in a dialog box that is the child of the sudo generated window or what? why can't I use sudo with cd? and what is the difference between gksudo and sudo?

Completly stumpt. Please help!!!![/QUOTE]

If I'm reading your post right, you want to access hda2 which is your Windows XP partition. You can't just "access" your Windows partition like that. You must first "mount" it. I could take you through the steps here but I'd be repeating what has been said countless times here in the forum and the Wiki. So, here are the links to mounting your hda2 Windows partition. Please bare in mind you must first know what type of file system Windows uses, NTFS or FAT32.

[https://wiki.ubuntu.com/MountingWindowsPartitions]("https://wiki.ubuntu.com/MountingWindowsPartitions")

[http://www.ubuntuforums.org/showthread.php?t=148056]("http://www.ubuntuforums.org/showthread.php?t=148056")

[http://www.ubuntuforums.org/showpost.php?p=846579&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=846579&postcount=8")

I want to reiterate one of the things said in one of the posts. Linux, Ubuntu in particular here CAN READ both NTFS and FAT32 partitions so reading them after they're mounted isn't much of a problem. **HOWEVER, writing to NTFS file system is still experimental and may result in data loss. You're strongly advised NOT to write to NTFS. **

If you need any further help, please don't hesitate to ask.

---

### Post by ajgreeny on 2006-03-28
Is your windows disk formatted ntfs?
If so you will have to accept defeat as far as writing to it from ubuntu is concerned, as linux does not yet have any (safe) way of writing or saving to a ntfs partition.
If it was fat32 you would be OK, but I don't know if it is safe to change the file system type of an existing windows setup, so can't help any further.  No doubt someone else will be able to help you.

---

### Post by meborc on 2006-03-28
welllllll... from your post i really don't read if you have mounted the windows partition already or not? ... just in case check this - [https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions)

now, if your win is on NTFS (winXP for example) then i DO NOT suggest you to try to write something there... as linux still has issues writing on NTFS... it has been done, but the last i heard of it, it ended quite badly...

the secure way to hava access to files both by win and ubuntu is to create a 3rd partition (fat32) which is readable/writable by both...

for more info, refer to - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

EDIT: WOW, ppl are fast... but at least we all share the ideas :D

EDIT2: ... and sudo is used in terminal/command line... gksudo is for graphical apps with 'pop-up' password prompt <- gksudo ;)

---

### Post by belikralj on 2006-03-28
I believe it is mounted because, there are two litle icons on my desktop, hda1 and hda2 that were there since instalation last night when I posted this thread. hda1 I wish to unmount permanently but even using sudo it was back this morning, while I have to use "sudo nautilus" to be able to only view the information which does contain all my windows folders. I think it is an ntfs partition but I'm not sure because I have no partitioning software on my windows machine. I'll check with gparted though and post again in a minut or two.

---

### Post by belikralj on 2006-03-28
hda1 is virtual fat while hda2 is ntfs.

the strange thing is that hda1 I can access without a problem but hda2 when I double click gives "you do not have permition to view this file". That is my problem and I'm sorry I didn't make it clearer sooner but I was very sleepy when I first posted this.

thell me if you need any more information to help me solve this because I'm shooting in the dark as to where the problem is so I don't know what to exactly post so you know the situation.

thanks very much for your posts.

---

### Post by AndrewCaul on 2006-03-28
Sounds like it wasn't mounted as NTFS correctly maybe. What's your /etc/fstab file look like?

---

### Post by sn123 on 2006-03-28
[QUOTE=belikralj]hda1 is virtual fat while hda2 is ntfs.

the strange thing is that hda1 I can access without a problem but hda2 when I double click gives "you do not have permition to view this file". That is my problem and I'm sorry I didn't make it clearer sooner but I was very sleepy when I first posted this.

thell me if you need any more information to help me solve this because I'm shooting in the dark as to where the problem is so I don't know what to exactly post so you know the situation.

thanks very much for your posts.[/QUOTE]
pls. to post the contents of your /etc/fstab file
```

$ cat /etc/fstab

```
By the way, this forum has multiple posts on getting ntfs partition to mount properly on Ubuntu.

S

---

### Post by belikralj on 2006-03-28
would changing /etc/fstab or where it is mounted halp me? because I don't want to mount hda1 or even have access since it seems to be an entirely windows boot oriented partition. But hda2 has all my files on it. Should I remount it somewhere inside the home folder where I do have permissions??

---

### Post by aysiu on 2006-03-28
[QUOTE=belikralj]hda1 is virtual fat[/quote] If mounted properly, you'll be able to read/write > while hda2 is ntfs. If mounted properly, this will be read-only.

> 
the strange thing is that hda1 I can access without a problem but hda2 when I double click gives "you do not have permition to view this file". That is my problem and I'm sorry I didn't make it clearer sooner but I was very sleepy when I first posted this.

thell me if you need any more information to help me solve this because I'm shooting in the dark as to where the problem is so I don't know what to exactly post so you know the situation. Follow these instructions:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If you have any further questions, just ask.

> would changing /etc/fstab or where it is mounted halp me? Changing *where* it's mounted won't help--changing *how* it's mounted will. > because I don't want to mount hda1 or even have access since it seems to be an entirely windows boot oriented partition. But hda2 has all my files on it. You can choose exactly what you want to mount or not mount--people have given you links to instructions for both FAT and NTFS. > Should I remount it somewhere inside the home folder where I do have permissions?? No. You can mount it anywhere. It matters only *how*, not *where*, as Windows partitions cannot be chowned or chmoded--they don't follow traditional Linux permissions.

---

### Post by Mustard on 2006-03-28
[QUOTE=belikralj]would changing /etc/fstab or where it is mounted halp me? because I don't want to mount hda1 or even have access since it seems to be an entirely windows boot oriented partition. But hda2 has all my files on it. Should I remount it somewhere inside the home folder where I do have permissions??[/QUOTE]

Let's see what your /etc/fstab looks like first and we will see what the problem might be.

See the previous post asking you to paste the contents of your /etc/fstab file in here.

---

### Post by aysiu on 2006-03-28
The terminal where you paste commands like *cat /etc/fstab* is in Applications > Accessories > Terminal (Gnome) or KMenu > System > Konsole (KDE)

---

### Post by belikralj on 2006-03-28
heres my original fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hdb1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


heres what I changed it ti after reading "http://www.tuxfiles.org/linuxhelp/fstab.html":

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    ro,noauto,nouser  0       0
/dev/hda2       /media/hda2     ntfs    rw,auto,user,sync,noexec   0       0
/dev/hdb1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,auto,sync  0       0


hope I didn't mess up to badly and that this halps  ](*,)

---

### Post by Mustard on 2006-03-28
I'd suggest changing your ntfs partition to this..

```
/dev/hda2    /media/hda2 ntfs  nls=utf8,umask=0222 0    0
```

and your vfat to this

```
/dev/hda1    /media/hda1 vfat  iocharset=utf8,umask=000  0    0
```

Then do a umount command on each of these partitions..

```
sudo umount /media/hda1
sudo umount /media/hda2
```

Then mount all entries in fstab again

```
sudo mount -a
```

---

### Post by aysiu on 2006-03-28
Try this instead: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
/dev/hda2 /media/hda2 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
``` Then ```
sudo umount /dev/hda1
sudo umount /dev/hda2
sudo mount -a
```

---

### Post by Mustard on 2006-03-28
Actually, just recalled you don't want to mount /dev/hda1 at all, so I would suggest you remove the line referring to /dev/hda1 in your fstab file completely, so you don't have that mounted at boot up anymore.

/me has a chuckle at myself and aysiu posting exactly the same answers at the same time. :)

---

### Post by belikralj on 2006-03-28
That did the trick!!! Huray!!!

You strongly recomended not to write to ntfs. I assume this didn't fix that fact. So I will heed that warning, and would like to know if there is a way to change file systems without loosing data. But that may be beyond my needs, it's just a point of interest.

Also could you explain to me what those lines actually did and what they mean?

the "iocharset=utf8,umask=000" and the "nls=utf8,umask=0222", Please Explain if you can.

Other than that Thank you very much! 
I look forward to the time when I can help others in this community.

---

### Post by meborc on 2006-03-30
[QUOTE=belikralj]That did the trick!!! Huray!!!

You strongly recomended not to write to ntfs. I assume this didn't fix that fact. So I will heed that warning, and would like to know if there is a way to change file systems without loosing data. But that may be beyond my needs, it's just a point of interest.

Also could you explain to me what those lines actually did and what they mean?

the "iocharset=utf8,umask=000" and the "nls=utf8,umask=0222", Please Explain if you can.

Other than that Thank you very much! 
I look forward to the time when I can help others in this community.[/QUOTE]

the piece about "utf8" means special characters 

umask=000 -> permissions ... you have to substract the number from 777 and you get the permissions given to that partition... in this case 777-000=777 :D

---


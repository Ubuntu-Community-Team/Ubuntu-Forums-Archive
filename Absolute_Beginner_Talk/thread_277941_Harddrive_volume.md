---
title: "Harddrive volume"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Tuxxx on 2006-10-15
Hello i just got ubuntu on my computer and i have a 30 gb harddrive and i have 2 partitions the first one is 25 gb and i cant open it on computer i dont understand why... when i press propertis it sais im not the owner and on another thing i opend it i dont remember what it was it said it was disabeld and unaccesable and that it was a fat32 hard drive the other partition is 2.5 gb and it is an extention 3 how can i make the partition 1 accesable? 

 ](*,) ](*,) :confused: :confused: :confused: :mad: :-k :-k

---

### Post by Klaidas on 2006-10-15
Dude, calm down...
Explain everything clearly, with commas and periods, and you don't need to include as much smiles as the forum lets you to...
If you do that, I'm sure you'll get a faster answer :)

---

### Post by docshawnc on 2006-10-15
Let's see what your fstab looks like.  Type:

cat /etc/fstab

and post the results.

---

### Post by Tuxxx on 2006-10-15
Ok   this is the story, when i installed ubuntu on my laptop yesterday i opend computer and then i double clicked 25.7 GB Volume and it said "Unable to mount the volume." and i went to a swedish forum and i tryed everything they said but nothing worked so they stopped awnsering me...
My 25.7 GB Volume is a Fat32 partition. I have 2 partitions one is 2.5 GB and the other is 25.7 GB and the small one works perfectly and the whole system is there and the other one (the big one) cant open it says im not the owner so i cant change it and it is unaccesable and i cant change that either can you tell me what to do?

---

### Post by Tuxxx on 2006-10-15
cat tux@Tux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# Manuellt monterat
/dev/hda1 /media/Lagring vfat ocharset=utf8,umask=000,shortname=mixed,uid=1000,gid=1000 0 0

---

### Post by docshawnc on 2006-10-15
ok - try replacing this line

/dev/hda1 /media/Lagring vfat ocharset=utf8,umask=000,shortname=mixed,uid=1000,g id=1000 0 0

with this line

/dev/hda1   /media/hda1    vfat   defaults,utf8,umask=007,gid=46 0   1

and then restart and see how it works

---

### Post by Tuxxx on 2006-10-15
how to replace it?

---

### Post by docshawnc on 2006-10-15
sudo gedit /etc/fstab

cut & paste

---

### Post by Tuxxx on 2006-10-15
ok i restarted but no diffrence...

but i looked at more detaild ... and it said you have to be the root something to mount hda1

---

### Post by Tuxxx on 2006-10-15
and i change the code ofcourse

---

### Post by docshawnc on 2006-10-15
Does /media/hda1 exist in your file system? 

type: ls /media

---

### Post by Tuxxx on 2006-10-15
No it doesnt.

---

### Post by docshawnc on 2006-10-15
go into terminal and type

cd /media

sudo mkdir hda1

restart and the volume should be there

---

### Post by Tuxxx on 2006-10-15
the volume isnt there and i still cant open it... what to do now?

---

### Post by AJLChase on 2006-10-15
Yeah I have the same problem. It says that you need permission to open up the drive. I would think typing a command in root and opening it up that way would work, but I am not sure how to do that.

---

### Post by DarkN00b on 2006-10-15
I have never done this before, but doesn't this have something to do with chroot and chown? I wish I could remember the commands.

---

### Post by anaconda on 2006-10-15
can you access the drive with file browser with root rights??

to start it type
```
sudo nautilus
```
in terminal.

Are you sure that your hda1 isn't the partitin where you have ubuntu installed?  You don't mount that partition, because it is already available.. that is the one where your home, and all the installed programs are..

---

### Post by Tuxxx on 2006-10-16
hda1 is 25 gb and it is my partition 1 and i have nothing on it i think and hda2 is 2.5 gb and i have filesystem on it how do i open hda1?

---

### Post by Tuxxx on 2006-10-16
i opend computer with gksudo nautilus /media and i tryed to change rights or what it is called and it said it culdnt and i tryed to open it and it said "mount: error in filesystemstype, wrong flag, wrong superblock on /dev/hda1 codepage is missing."   what does that means?

---

### Post by gn2 on 2006-10-16
> **Tuxxx said:**
> i opend computer with gksudo nautilus /media and i tryed to change rights or what it is called and it said it culdnt and i tryed to open it and it said "mount: error in filesystemstype, wrong flag, wrong superblock on /dev/hda1 codepage is missing."   what does that means?

It could mean you should try PCLinuxOS, where all access to partitions and hard drives can be done with a GUI. Vastly superior.(just my opinion)

---

### Post by Tuxxx on 2006-10-16
how to i do that??? is it ubuntu or what?

---

### Post by gn2 on 2006-10-16
> **Tuxxx said:**
> how to i do that??? is it ubuntu or what?

It is another distribution of Linux, and is more user friendly for new users.

[http://www.pclinuxos.com/page.php?7](http://www.pclinuxos.com/page.php?7)

---

### Post by Tuxxx on 2006-10-17
ok ty guys

---


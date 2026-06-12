---
title: "Accessing NTFS hard drive"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by 137.Nexxus on 2005-08-26
i know a bit down there  is someone with a similar prob but i didnt want to post in his/he thread. my prob is that i have a ntfs hard drive for storage <15gigs of media> conneccted to this machine. i use both windows and linux on the main drive. but i want to browse the files on  the ntfs drive that is just storage. <it has no OS on it> is there a quick way to do it? if all esle fails another machineahas same data on it and i canaccess those files viasamba but i wana use the physical drive instead if that makes any sence lol

---

### Post by grim42 on 2005-08-26
See [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by 137.Nexxus on 2005-08-26
ok ive monted it. now as ima newbie, where do i click to access the files? i can browsw hda1 but i dont see hda2 if in browser i click hda2/  i get a malformed url error. did i screw up?

---

### Post by Kapre on 2005-08-26
[QUOTE=137.Nexxus]ok ive monted it. now as ima newbie, where do i click to access the files? i can browsw hda1 but i dont see hda2 if in browser i click hda2/  i get a malformed url error. did i screw up?[/QUOTE]
 137.Nexxus - If you followed the link on how to mount your NTFS drive, you can browse/look for it in your Computer->look for Media (click on it) and there you can see the NTFS drive.

K

---

### Post by 137.Nexxus on 2005-08-26
ok i followe the guide but it says in infocenter /dev/hda2/ under mount options "defaults,errors=remount-ro i just  realised hda 1 is my storage i think. but when i follow the command :
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

it pulls upa list like something was done wrong  ](*,)

---

### Post by Knyven on 2005-08-26
are you sure you typed, in the root terminal the:

[COLOR=Red]sudo mkdir /media/windows

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222[/COLOR]

---

### Post by 137.Nexxus on 2005-08-26
im using koinsole on the command line it says :nexx@serve~$
do i have to put something in to access root?

---

### Post by 137.Nexxus on 2005-08-27
ok i did all that i can see the drive but when i try to access files in it it says " mount: can,t find /dev/hdb1 in /ect/mtab"

it was working and when i rebooted there was a thing called xserver that was locking up the pc so i rebooted it via the button

---

### Post by wellery on 2005-08-27
[QUOTE=137.Nexxus]ok i did all that i can see the drive but when i try to access files in it it says " mount: can,t find /dev/hdb1 in /ect/mtab"

it was working and when i rebooted there was a thing called xserver that was locking up the pc so i rebooted it via the button[/QUOTE]


I'm not sure exactly what you are talking about but if you want to be able to acces the ntfs partition everytime you restart your computer you are better off following this:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by RobArson on 2005-08-27
i'm no expert, but i recently did the same thing with fat32. (and i assume its the same, although you probably can't write to the NTFS filesystem with ubuntu without some extra work)

first, you have to mount your partition. You can do fdisk /dev/hda to check out your partition table to make sure you know which partition is your NTFS.

Then you can do 

mount /dev/hda? /somenamehere

where the first argument is the partition you want to mount and the second argument is a name you wanna assign to it.

--------->>>>>however, next time u reboot, it won't be mounted anymore!

so you have to go to etc/fstab and change it so it mounts everytime u log in.
add a line in the format of the lines already there. Something like this:

/dev/hda? /somenamehere ntfs defaults 0 0

First arg is partition, second is name, third is file system.
i'm not sure what the last 3 arguments do exactly, but that should work with no problems. 

save the file and from now on, that partition will be mounted every time u log in!
to access the file, just cd to /somenamehere.

I highly doubt you will have full read/write priveleges but you should be able to read without a problem.


Hope that helps and be advised, I'm just assuming its the same as mounting to a fat32 partition.

---


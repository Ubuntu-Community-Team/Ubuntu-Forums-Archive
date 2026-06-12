---
title: "Show partition in &quot;Places&quot; ?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-08-24
How can I show a certain partition in "Places" ?  I have dev/hda1 and dev/hda5 there,and would like to put dev/hda6 there ! Thanks :p

---

### Post by meng on 2006-08-24
Where am I seeing this? Is there a screenshot you meant to post?

---

### Post by Drakkor on 2006-08-24
Lol,it seems that I can't make a screenshot while the "Places" menu is open !
I hit "Print Screen" and nothing happens.

---

### Post by meng on 2006-08-24
Just open the file browser and your Places should be in the left panel. But while we're waiting ... are /dev/hda1 and /dev/hda5 mounted? and is /dev/hda6 mounted?

---

### Post by kinematic on 2006-08-24
for some reason your partitions only show in places if you use /media to mount them......go figure :rolleyes:

---

### Post by Drakkor on 2006-08-24
Maybe because it's on a different drive? fstab here:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto,exec    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /Foghorn        ext3    rw,user,auto,exec    0       0

---

### Post by Drakkor on 2006-08-24
But it's funny hda1 and 5 are there and not in media ???  :confused:

---

### Post by meng on 2006-08-24
Can you not navigate to /Foghorn in the file browser, then Add Bookmark?

---

### Post by Drakkor on 2006-08-24
Great !! meng, that worked perfectly !! Thanks ! :biggrin:

---

### Post by kinematic on 2006-08-24
> **kinematic said:**
> for some reason your partitions only show in places if you use /media to mount them......go figure :rolleyes:

that's what i was told by the local ubuntu guru.....guess he's not so much of a guru :mrgreen: 
well...at least i've learned something new :D

---

### Post by meng on 2006-08-24
Well you can specify any folder to appear in Places, but mounting within /media means it also appears in My Computer.

---

### Post by heather on 2006-08-24
seems i was able to get the mounting issue resolved
but im having problems with adding permissions to
read only drives

i have 2 parrtitions
linux and xp

i have two drives besides that
one is SATA
the other IDE
i am able to read but i cant write to them
even with the chmod commands

any advices?


thank you

---

### Post by tzulberti on 2006-08-24
> **heather said:**
> 
now i know byt default my drives are premounted
i really dont want them to automaticly mount




If you don't want you partionts to be auto mount, write in the fstab th noauto option for that partition

> **heather said:**
> 
i wanna understand exactly how to mount them manually


Recommended: man fstab, man mount

> **heather said:**
> 
by default i belive my drives werein /media folder
but i wanted to make them this way
/drives/Software
so being that im not logged in as root
i do the sudo command

mkdir /drives/software

now in  my fstab file i have
/dev/hdb1       /drives/Software/     ntfs

i notice sometimes i get a message about mtab file
must i mess with that file as well as fstab
very confused here


Maybe that message appears becuase you are not writting the line correctly. It should be something like:
/dev/hdb1       /drives/Software/     ntfs     defaults     0      0


> **heather said:**
> 
anwyays back to mounting

i then used the command
mount /dev/hdb1

when i peek inside the directory from a terminal
cd /drives/Software
ls

i can see the files there

yet i dont see the drive in computer at all
and when i do at times i cant even get permission to change permissions.even from root

if anywone can possibly walk me through id be grateful

thank you

heather

Neither root or normal user have the permission to write on a ntfs partition. Look on the how-to section for more information about how to do this...

I hope that i have helped you

---

### Post by heather on 2006-08-25
Thank you all for your help
seemws to be workign now
my fstab file is a little differnt
i used

/dev/hdb1 /drives/Backups ntfs user,umask=1000,ro,noauto

seems to work fine letting me mount manually
but i like the way the icons use to show up on their own on desktop when mouting or unmouting

seems to only work when i use the /media folder then my own
how can i change that

thank you

---


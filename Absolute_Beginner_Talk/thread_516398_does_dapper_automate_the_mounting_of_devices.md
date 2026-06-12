---
title: "does dapper automate the mounting of devices"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by rufi_dukes on 2007-08-03
coz i got a new machine a few days ago with feisty pre-installed and i can't watch a video;
not ready for the all the hard work, want a bit of straightforward pleasure first...

so...
was thinking of installing dapper (a copy of which i have);
but would this mean that i could use my dvd drives to burn iso, watch dvds and stuff?
coz otherwise, if i was still stuck with drives i couldn't use, then i'm no better off


thx,
rufus

---

### Post by 505 on 2007-08-03
Yes, dapper automounts discs, but so does Feisty. Feisty is a newer version than Dapper, so most of the time you're better of with Feisty. Is it that CD's and DVD's do not mount (try it with a data disc), or that video does not work. Out of the box, no Ubuntu installation plays divx and wmv videos or DVD movies. You need to install some libraries for that. Google for 'ubuntu restricted formats'.

---

### Post by rufi_dukes on 2007-08-03
> **505 said:**
> Yes, dapper automounts discs, but so does Feisty. Feisty is a newer version than Dapper, so most of the time you're better of with Feisty. Is it that CD's and DVD's do not mount (try it with a data disc), or that video does not work. Out of the box, no Ubuntu installation plays divx and wmv videos or DVD movies. You need to install some libraries for that. Google for 'ubuntu restricted formats'.


this is what i get from 
cat etc/fstab

michael@tester-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=65337b33-b4ca-45cf-a42e-00c7cd597bfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=238d9f43-ae49-4a1d-959f-711e0344bbe2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
michael@tester-desktop:~$ df -hT
Filesystem Type    Size Used Avail Use% Mounted on
/dev/sda1     ext3    288G  3.0G  271G   2% /
varrun       tmpfs   1005M  100K 1005M   1% /var/run
varlock      tmpfs   1005M     0 1005M   0% /var/lock
procbususb   usbfs   1005M  124K 1005M   1% /proc/bus/usb
udev         tmpfs   1005M  124K 1005M   1% /dev
devshm       tmpfs   1005M     0 1005M   0% /dev/shm
lrm          tmpfs   1005M   33M  972M   4% /lib/modules/2.6.20-16-generic/volatile
michael@tester-desktop:~$ mount


when i try to watch a movie in totem it tells me that 
totem can't find the plugin to run movie in cd0

---

### Post by rufi_dukes on 2007-08-03
actually, i've already got the restricted software from third party and installed it successfully;
it's as if totem is all dressed up and ready to play but can't read a dvd drive;
it says:

"Totem could not play 'dvd:///media/cdrom1'.
There is no plugin to handle this movie."

r

---

### Post by rufi_dukes on 2007-08-03
the other thing that isn't so great with feisty is the way it won't let me hibernate or suspend without stuffing up the colours in the screen..
i have to resort to a complete restart to clear it again....

---


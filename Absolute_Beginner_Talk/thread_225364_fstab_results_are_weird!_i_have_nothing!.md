---
title: "fstab results are weird! i have nothing!"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by noodles12 on 2006-07-29
I have the mounting root filesystem problem where is says 
cannot access tty: job control turned off
it does not recognize my sda4 paritition where linux is installed.

i type in sudo gedit //etc/fstab   (using a live cd)
my results are

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

I thought i was suppose to get a list of parititions =/. 

What does this mean?

---

### Post by Dr. Nick on 2006-07-29
not sure on your origional problem, but the fstab you are seeing most likely is the one from the cd, not the one that is on the installed version of ubuntu. To see that one you need to mount the partitions using the live cd

unless it was a typo that is also 1 too many "/s" should just be

sudo gedit /etc/fstab

this page my help you mount your linux partitions for use if they are not done already,

[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

Hopefully someone with a bit more expierence with fstab/live cds can be of more help

---

### Post by noodles12 on 2006-07-29
I tried to mount my sda4 partition and it says special device /dev/sda4 does not exist. 

In gparted i see the following
Paritition File       size    used         unused          flags
           system
/dev/sda4  ! ext3     7.81 GB  --           --               --

the ! is inside a triangle and says:

status: not mounted
Unable to read the contents of this filesystem! because of this some operations may be unavialable. did you intall the correct plugin for this filesystem?

---


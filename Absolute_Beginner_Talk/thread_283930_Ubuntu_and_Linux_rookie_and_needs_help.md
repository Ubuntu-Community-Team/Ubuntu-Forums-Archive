---
title: "Ubuntu and Linux rookie and needs help"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by trleslie on 2006-10-24
Recently i loaded Ubuntu on my imac using parrallels virtualization software. It loaded up allright however although seeing the cd in the computer it can't read it. Is there something i need to download to make this work. I am quite new to this whole linux thing so i am as green as they get,
Would appreciate some direction
Thanks
trleslie

---

### Post by Hmarroqu on 2006-10-24
make sure u burn the iso image on to a disk and check it to make sure its on there and it doesnt appear as a bunch of files. the bunch of files wont work like that:-?

---

### Post by trleslie on 2006-10-24
Sorry i didn't make my question very clear.
 I did load the Linux operating system and it works fine. However now when i try to read a cd on  Ubuntu, the desktop shows a cd but when i click on it there is nothing on it. Whether it is files, music or a program nothing shows as being on the cd even though there is files on it. I feel maybe i didn't download or install something that is used to read cd from the drive.
Thanks for your thoughts
trleslie

---

### Post by MyAnda on 2006-10-24
I have never used parrallels...is there a cdrom setting somewhere that should be adjusted? if I was having this issue I would want to know
1.is the cd fine (do you see everything you expect from the host/mac side of things)...did you try a different cd 
2.is the cd getting properly mounted?
remove it/eject it, and put it back in...does your file manager popup?
from a terminal (applications>accessories):
the command "mount" will give you a list of currently mounted filesystems...look for something like /media/cdrom0....post the output

that is probaly a decent place to start

---

### Post by trleslie on 2006-10-25
Thanks for the input, for what i can see the parrallels is set up right but that could easily be the problem. I opened terminal and typed mount and this is what i got
I couldn't cut and paste so i typed it out by hand. I hope i got it right


/dev/hdal on / type extr3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on/lib/modules/2.6.15-27-386/volatile type tmpfs (rw)

Thanks

---

### Post by Ben Sprinkle on 2006-10-25
```

mount '/media/cd1'

```
Where cd1 is, you put the correct name of your cd. (Like hda1, sda1 etc.)

---

### Post by MyAnda on 2006-10-25
was the cd in when you ran "mount"...if so, looks like it is not mounted
you could do as synectics suggested and mount it...if you are not sure what to put in, try (with the cd in) "mount -a" this will try to mount everything in /etc/fstab...(this is a file worth looking at and getting comfortable with)...also, by having a look at it (cat /etc/fstab ...or whatever you perfer) it will let you know what device it is using e.g.
the interesting line in mine looks like
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
 ^^^^^^device    ^^^^^^^ mount point

so typing "mount /media/cdrom0" will mount my cdrom
"man mount" will give you more info

---


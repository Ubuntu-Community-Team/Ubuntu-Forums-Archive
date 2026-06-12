---
title: "How can I find out what HDD my home dir belongs to?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by i.herteleer on 2006-02-06
(See title)
I have an exam coming up soon, and this is one of the questions I might be asked. Using fdisk -l i found all the hard drives and partitions, but it still doesn't exactly answer the question...
Any ideas?
Thanks for the help :)
Inti

---

### Post by krusbjorn on 2006-02-06
cat /etc/mtab gives you a list of all mounted partitions and where they are mounted.

---

### Post by i.herteleer on 2006-02-06
Is the first one in the list produced by cat /etc/mtab the HDD on which my HOME dir is then (since it's the first to be mounted i assume...)?
And what exactly is the mtab folder? 
Thanks

---

### Post by krusbjorn on 2006-02-06
[QUOTE=i.herteleer]Is the first one in the list produced by cat /etc/mtab the HDD on which my HOME dir is then (since it's the first to be mounted i assume...)?
And what exactly is the mtab folder? 
Thanks[/QUOTE]

Not really. For reference, here is my mtab file:
> /dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0tmpfs /lib/modules/2.6.12-10-686/volatile tmpfs rw,mode=0755 0 0
/dev/sda9 /home ext3 rw 0 0
/dev/sda7 /tmp ext3 rw 0 0
/dev/sda6 /usr ext3 rw 0 0
/dev/sda8 /var ext3 rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0


As you can see, /dev/sda9 is mounted at /home, meaning the 9th partition on my first SATA drive. If it says hda its your first IDE drive, hdb your second etc. Sda means "special device" (if i remember correctly, right?) and generally sata drives, external hard drives and stuff like that are classified as sda. If you have no partition mounted at /home, your home folder is situated on your root partition (the one mounted directly at /). In my case "/dev/sda1"

Edit: Oh. And the mtab file is just a simple file showing which partitions are mounted, and where. You can open it in a plain text editor if you dont like the command line.

---

### Post by i.herteleer on 2006-02-07
Is the file mtab in /etc/ simply a list of mounted devices? cat /etc/mtab seems to return the same as the command mount, so i assume it is :) but am i right?
Thanks

---

### Post by krusbjorn on 2006-02-07
Yeah it is.

---


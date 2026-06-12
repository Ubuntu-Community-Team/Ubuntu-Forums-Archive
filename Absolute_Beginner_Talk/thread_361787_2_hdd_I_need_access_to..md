---
title: "2 hdd I need access to."
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Bubs on 2007-02-14
ok I just read the sticky on edgy and am downloading dapper now to install.  I just loaded edgy on my MAIN desktop computer!  and I have two other hard drives that I used in windows as storage.  I believe I wouldn't be able to write to them, but is there a way I could access them?  I want to move some things off then reformat for linux.  

and the reason I'm moving to dapper is I heard it was the way to go if you want stability.  and I just bought a new 19" widescreen and I can't get it to go to 1440x900.  I heard dapper does that automatically.  I don't need bleeding edge on this machine I need it to work.  the laptop though...  I can bleed until I pass out on that!

but hard drives I need answers for the hard drives.  and If I go to the device manager I can see 2 maxtor hard drives (the ones I want!) but I don't know how to access them.


bubs

---

### Post by tronica on 2007-02-14
heres a quick guide on mounting windows drives

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")

---

### Post by Bubs on 2007-02-14
thanks for the link!!  I haven't tried the mounting of the hdd's but on that page I found a link to a script called "envy" which downloads and install the newest ati and nvidia drivers for you then reconfigures x.  so I have a 1440x900 resolution now!!

so I don't need to change from edgy (although I still might... i'll give it a go)

---

### Post by Bubs on 2007-02-14
and the instuctions worked thank you for the help

---

### Post by tronica on 2007-02-14
glad to hear it. :)

---

### Post by Bubs on 2007-02-14
ok here's another one that should be easy.  I checked the guide you showed me but didn't see anything.

how do I format and mount a harddrive to use as extra storage?

---

### Post by tronica on 2007-02-14
well to format it, i use gparted

> sudo apt-get install gparted

then it will you need to mount it

make a directory to mount it with

> cd /media

> sudo mkdir Storage

> sudo chmod 777 Storage

then you need to add it to fstab so it will automaticly be mounted on boot

> sudo gedit /boot/grub/menu.lst

and add a line at the bottom like this

> /dev/hdb2 /media/Storage ext3 defaults 0 2

the hdb2 could differ, you will have to check that when you format it .

---

### Post by frup on 2007-02-22
> **tronica said:**
> well to format it, i use gparted



then it will you need to mount it

make a directory to mount it with







then you need to add it to fstab so it will automaticly be mounted on boot



and add a line at the bottom like this



the hdb2 could differ, you will have to check that when you format it .

 Randomly found this, I might be wrong but i believe you mean /etc/fstab not the grub menu.lst

---


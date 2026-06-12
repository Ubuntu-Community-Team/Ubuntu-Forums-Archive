---
title: "help needed for my dvd"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-03-04
my dvd drive opend when i typed "mount /media/cdrom0" in terminal

but my drive was not ejecting out dvd

and i got this 

total 10
lrwxrwxrwx 1 root root 6 2008-03-03 12:01 cdrom -> cdrom0
dr-xr-xr-x 1 root root 10240 2008-03-03 17:35 cdrom0

when i typed "ls -l /media"

plz help me and explain me in detail what is the cause of problem

---

### Post by kesman on 2008-03-04
You always have to mount as sudo, and I have no idea what are you talking about. You typed mount /media/cdrom0 and the cd-rom tray opened? That should not happen as far as I know. Mount is only used as sudo, and with two parameters, "sudo mount /place/to/mount/from /place/to/mount/to".

---

### Post by phanipalagummi on 2008-03-04
sorry i was not clear in my post 

previously my dvd was not detecting, when inserted the dvd in drive
when later i typed "mount /media/cdrom0" my dvd was detecting
but i can not eject the dvd drive it says some thing like"can not eject the volume"
could u help me in removing the disk 
and one more thing when i type this"ls -l /media" in terminal
i m getting 

total 10
lrwxrwxrwx 1 root root 6 2008-03-03 12:01 cdrom -> cdrom0
dr-xr-xr-x 1 root root 10240 2008-03-03 17:35 cdrom0

could u help me please
and please tell me the reason why it happend so

---


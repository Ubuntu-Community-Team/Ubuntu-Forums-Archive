---
title: "cant connect to x server, gui messed up?"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2006-10-25
ok well i was using a guide and was messing with some /etc/xconfig file or something and was changing input device mouse settings and i hit CTRL ALT BACKSPACE, and it got all messed up and says "cant connect to x server" some gui error, how do i fix this?

---

### Post by CatKiller on 2006-10-25
sudo dpkg-reconfigure xserver-xorg

---

### Post by TheNemeses on 2006-10-25
hey i think the file was like /etc/x11/xorg.conf does that have somethign to do with it?

---

### Post by CatKiller on 2006-10-26
/etc/X11/xorg.conf, yes. The command I gave you will help you get that file back as it should be.

---

### Post by TheNemeses on 2006-10-26
ahh when i try to do it it gives me all this stuff and half of it idk what to put it and then at the end it says some error like it couldnt overwrite the file or something, is there some way to restore the file from my ubuntu cd or something

---

### Post by taurus on 2006-10-26
Yeah.  You can boot with the LiveCD, mount your harddrive where / partition is located, assuming to /mnt/ubuntu, then copy /etc/X11/xorg.conf (from LiveCD) to your harddrive, /mnt/ubuntu/etc/X11/xorg.conf.  Unmount your harddrive, reboot, and remove the LiveCD...

```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming it's an ext3 filesystem and it's the first partition of your master harddrive...)
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
sudo umount /mnt/ubuntu

```

---

### Post by TheNemeses on 2006-10-28
ok so i stick in the cd go onto the ubuntu live desktop open a terminal and type in the code you said?? or do i boot from ubuntu from my hd and leave my cd in the drive and do the code from the screen?

---

### Post by TheNemeses on 2006-10-29
it says cant stat ` /etc/x11/xorg.conf file doesnt exist

---

### Post by CatKiller on 2006-10-29
> **TheNemeses said:**
> it says cant stat ` /etc/x11/xorg.conf file doesnt exist

Careful with your typing, there.

---

### Post by taurus on 2006-10-29
> **TheNemeses said:**
> it says cant stat ` /etc/x11/xorg.conf file doesnt exist
It's X11 as in capital X and number 11--X11...

---

### Post by TheNemeses on 2006-10-29
oh, linux is cap sensitive with all code? ok that might explain why a few codes dont work

---


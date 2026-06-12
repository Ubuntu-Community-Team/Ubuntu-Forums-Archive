---
title: "Need default xorg.conf code !"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by NovaNine on 2007-05-07
Hey guys.

Anyone has the default code for the /etc/X11/xorg.conf file ? I've messed it up and need it back.

Thanks :)

---

### Post by ayoli on 2007-05-07
just run this command in a terminal (sudo will prompt you for your user password):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and your X will be reconfigured as it was after first install.

---

### Post by taurus on 2007-05-07
You might have a backup copy in /etc/X11.

```
ls -la /etc/X11
```
Otherwise, reconfigure it with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by NovaNine on 2007-05-07
Thanks, but I'm looking for the code itself. And no, i don't have the backup :(

Anyone has it ? I'm going to manually edit from the live CD :p

---

### Post by rocknrolf77 on 2007-05-07
What graphics card do you have? Why not use ```
sudo dpkg-reconfigure xserver-xorg
```

The xorg.conf file depends on the hardware. It's not the same for everyone.

If you have a nvidia card you can do a ```
sudo nvidia-xconfig
```

---

### Post by Nythain on 2007-05-07
hehe... if all else fails... you can resort to the good ol' boot up the LiveCD, open up that xorg.conf and email it to yourself... or just mount a partition and copy it over... it will pretty much be a vanilla xorg.conf for your hardware as detected and setup by the livecd

---


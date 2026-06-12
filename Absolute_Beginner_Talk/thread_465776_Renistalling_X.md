---
title: "Renistalling X?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-06-06
My graphics driver and the X11 folder are totally screwed (right now I'm without any xorg.conf file and if I put one in, the X won't start) so is there any way to reinstall these packets and return to the state that was up when I installed ubuntu? 

I heard of the command apt-get reinstall but I don't really know what packets to reinstall. I guess it would be xorg-xconf or something like this.

Please help!

---

### Post by paydaydaddy on 2007-06-06
I do not have the answer for you, but I am sure that somebody else will. You can help by posting which distro you are using.

---

### Post by Boris-- on 2007-06-06
Ubunutu feisty 7.04 of course :)

---

### Post by mkoehler on 2007-06-06
If you reinstall "gnome" (if you're running gdm), you should solve your problems

---

### Post by Crafty Kisses on 2007-06-06
You can try to reconfigure your X Server file by trying the following:
```
sudo dpkg-reconfigure xserver-xorg
```
If that fails, and you backed up the X Server file you can recover it by doing the following:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

---

### Post by majed on 2007-06-06
> **mkoehler said:**
> If you reinstall "gnome" (if you're running gdm), you should solve your problems

This is an overkill.. 

You can go to synaptic and search for xorg and then reinstall that package.. or from the command line:

> 
sudo apt-get --reinstall install xorg


---


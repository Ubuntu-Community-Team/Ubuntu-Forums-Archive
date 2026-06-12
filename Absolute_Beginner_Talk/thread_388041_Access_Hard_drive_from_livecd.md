---
title: "Access Hard drive from livecd"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Crisuntu on 2007-03-19
Hello guys
Recently I installed Ubuntu on my Athlon XP 1700+ with a gforce2 of 64MB.
The installation process went fine and the system worked pretty good. However, as for the resolution, the only options I was given were "640x480" and "800x600". The resolution I needed was not available ("1024x768")
Someone told me to add the resolution manually to the xorg.conf file, but when I rebooted the monitor it showed "out of range".
I ran the "live CD" to check this file and restore it, but I cannot access the hard drive from it. So, does anybody know how can I access the hard drive from the live CD to modify my configuration.

Thanks
See you,

Cristian

---

### Post by mahiyar on 2007-03-19
Well on booting from the live cd, you run the >sudo fdisk -lu command from the CLI (terminal). Observe on which partition your linux is installed (like hda1 etc)and then mount the partition. This link is a good guide to mounting partitions [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

---

### Post by bodhi.zazen on 2007-03-19
Mount it ...

Assuming your ubuntu root is /dev/hda1 :

```
sudo mount /dev/hda1 /mnt
```

Now edit /mnt/etc/X11/xorg.conf or restore from back up ;)

If you do not know your root partition : ```
sudo fdisk -l
```

If you do not have a back up of a working xorg.conf, open a terminal and type "I will back up system files before I edit them" 100 times :p

---

### Post by Crisuntu on 2007-03-19
Well, I did everything you told me. Now when I try to edit the file it says the following:
                                "not write permissions to edit /mnt/etc/x11/xorg.conf"

I don't know if this is silly. I try to open xorg.conf with gedit using the sudo command to 
see if I can modify it, but when it opens the file it is empty. I guess it is opening the 
livecd xorg.conf file even though Ubuntu's partition is mounted.
I Don't know what to do to unlock it.

Thank you for your help,

Cristian

---

### Post by bodhi.zazen on 2007-03-19
Asuming you mounted your ubuntu partition at /mnt :

```
gksudo gedit /mnt/etc/X11/xorg.conf
```

If you used something other then /mnt you will need to adjust accordingly ...


FYI: You should use gksudo with any graphical (gui) program, sudo for CLI ...

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Crisuntu on 2007-03-19
I successfully edited my xorg.conf file.

Thank you so much for your thorough explanation.

Have a good day,

Cristian

---

### Post by bodhi.zazen on 2007-03-19
You are most welcome.

If you would be so kind as to mark this "resolved" 

Saves time on the part of others looking to help if they can see you are up and running ;)

---


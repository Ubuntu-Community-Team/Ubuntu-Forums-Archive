---
title: "Dude, where's my Grub.conf"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by C. M .Hughes on 2007-03-03
Hi all,
I'm a total Linux Noob, but am in love with the whole concept. I have a Grub question for anyone that's interested.

I have two hard drives, hda, and hdb. I installed Ubuntu onto a partition on hdb, and had Grub install onto hd0 (which I know is Grub's way of saying hda). This means that Grub comes up everytime I boot my computer, which is what I want. I have a dual boot with XP.

My question is, where is my grub.conf file? Because I've installed Grub on a separate drive from the drive that Linux is on, I can't find it in 'the usual' boot/grub location.

Any help would be greatly appreciated.

---

### Post by Ehnvis on 2007-03-03
In ubuntu the file is called menu.lst so look for that one instead, usually under /boot/grub/menu.lst.

---

### Post by Gerard Barberi on 2007-03-03
it's in

/boot/grub/menu.lst

---

### Post by C. M .Hughes on 2007-03-04
Thank you very much chaps, that is brilliant. 

Once I worked out to edit (and save!) it using 

sudo gedit menu.lst

everything is great! Cheers again.

---

### Post by taurus on 2007-03-04
> **C. M .Hughes said:**
> 
**sudo gedit menu.lst**


It is NOT a good idea to use "sudo gedit".  If you want to use gedit, you should try to use it with gksudo.

```
gksudo gedit menu.lst
```
or
```
sudo nano -Bw menu.lst
```

---

### Post by Denn1s on 2007-03-04
i knw this may not be the rigth place to ask, but why shall we not use sudo gedit? 

ps. this posts title is great!!!

---

### Post by taurus on 2007-03-04
> **Denn1s said:**
> i knw this may not be the rigth place to ask, but why shall we not use sudo gedit? 

ps. this posts title is great!!!

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Denn1s on 2007-03-04
i see, thanks for the quick reply, it was iluminating, i really didnt had an idea

---

### Post by raminv2 on 2007-11-09
Thanks guys...
it fixed my problem and made me wonder why the hell we are using Microsoft....

---

### Post by spideygal on 2007-11-09
> **taurus said:**
> It is NOT a good idea to use "sudo gedit".  If you want to use gedit, you should try to use it with gksudo.

```
gksudo gedit menu.lst
```
or
```
sudo nano -Bw menu.lst
```

Neither of those commands work for me, I get a blank file, however if I use gksu nautilus I have no problems with getting the menu.lst.

???

---

### Post by jordanmthomas on 2007-11-09
Instead of menu.lst, try the full path:  (odds are you're not currently in the directory /boot/grub, right?)
```
sudo nano  -w /boot/grub/menu.lst
```

---

### Post by Duck2006 on 2007-11-09
Or

gksudo gedit /boot/grub/menu.lst

---

### Post by spideygal on 2007-11-09
Thanks.
:lolflag:

---


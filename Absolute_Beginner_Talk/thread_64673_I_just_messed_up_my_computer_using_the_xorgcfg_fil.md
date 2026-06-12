---
title: "I just messed up my computer using the xorgcfg file?"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by spfdz on 2005-09-11
I was searching the forum on how to change my resolution to a higher supported one.  I came across a post where I was suppose to edit or write a xorg.cfg file. Pretty much I ran through the wizard, and now my computer doesn't boot up. The farthest I can get is entering in my username and password. Then the screen says spfdz@ubuntu and that's it. There's no GUI at all. 

Can anyone help me out on this? I'm assuming I selected the wrong hertz/sync rates. I just don't want to reformat again...

---

### Post by aysiu on 2005-09-11
Did you make a backup copy of your xorg.conf?
If so, you can just copy the backup over the new one.
Something like ```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
If not, you may be able to edit the xorg.conf with nano ```
sudo nano /etc/X11/xorg.conf
```

---

### Post by krusbjorn on 2005-09-11
You can also reconfigure your xorg.conf file with step by step instructions by typing

sudo dpkg-reconfigure xserver-xorg

---

### Post by spfdz on 2005-09-11
[QUOTE=krusbjorn]You can also reconfigure your xorg.conf file with step by step instructions by typing

sudo dpkg-reconfigure xserver-xorg[/QUOTE]

Hmm that saved me from that black command line. But I still have a lower resolution. I thought I changed the resolution in that wizard to 1280x1024 too :(

---


---
title: "gksudo gedit /etc/X11/xorg.conf show nothing"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-02-06
I looked through the 5 similar posts that popped up ( by the way that is an excellent thing there saves time searching) but I could find the answers I need for some reason after I rebooted I lost ( I think its called xorg.conf) and also the backup is not to be found. I also must state that I am completely new to this I am coming from Windows and really want to learn linux because to me windows sucks

---

### Post by emarkd on 2008-02-06
Ummm... are you sure?  Did your computer boot properly into a graphical environment?  Are you sure you're typing it correctly?  Remember that Linux is case sensitive, so make sure you're getting that X11 capitalized.

---

### Post by Tatty on 2008-02-06
Did you make sure you capitalised the X in X11?

I always forget to do that, and end up staring at a blank file.

---

### Post by ptn107 on 2008-02-06
You can rebuild your xorg.conf file.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mikewhatever on 2008-02-06
Usually, the problem is a non-capitalized x in X11. Lots of users either forget or do not know in the first place that Terminal is case sensitive. Just to make sure the file exists, post the output of <ls /etc/X11>.

---

### Post by Shadowmeph on 2008-02-06
this is what I typed in gksudo gedit /etc/X11/xorg.conf 
thank you ptn107 I just tied that and got this
paroxysm@paroxysm-desktop:~$ gksudo gedit /etc/X11/xorg.conf
paroxysm@paroxysm-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
md5sum: /etc/X11/xorg.conf: No such file or directory

---

### Post by ptn107 on 2008-02-06
Don't type the command in your xorg.conf file.  Just type it as is at a terminal prompt.

ex.
**ptn107@ptn107-desktop:~$** sudo dpkg-reconfigure -phigh xserver-xorg

If it still complains that the file xorg.conf does not exist, type this at a terminal to make an empty one:
```
sudo touch /etc/X11/xorg.conf
```

then try this again
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Shadowmeph on 2008-02-06
> **ptn107 said:**
> Don't type the command in your xorg.conf file.  Just type it as is at a terminal prompt.

ex.
**ptn107@ptn107-desktop:~$** sudo dpkg-reconfigure -phigh xserver-xorg

If it still complains that the file xorg.conf does not exist, type this at a terminal to make an empty one:
```
sudo touch /etc/X11/xorg.conf
```

then try this again
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thank you so much I was starting to lose some water weight there for a while because of the sweat starting you just save me and thank you to everyone else for your suggestions and help :)
mnow the only thing stopping me from totally using Gutsy is being able to get my tv working from my s video output off my Video card so I can watch all my downloaded things that I watch through windows also my stupid ati driver mesa problem I will search for those though thank you again :)

---


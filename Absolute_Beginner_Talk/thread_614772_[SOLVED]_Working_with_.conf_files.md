---
title: "[SOLVED] Working with .conf files"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-11-16
I want to use the touchpad configuration tool, however, I get an error message stating that I need to turn it on in the xorg configuration file.  It states that I need to add the option "SHM Config" to on in the
touchpad section of /etc/X11/xorg.conf .  How do I do this?  how do I open the config file?
Thanks,
Cygnis1

---

### Post by PeterJS on 2007-11-16
.conf files are just text files, so any old text editor will do. One thing to be aware of is that /etc/X11/xorg.conf is owned by root and therefore isn't directly writeable by your user account. But if you open a terminal and run: sudo <texteditor>, the texteditor will run with elevated privilages that can write to the file.

---

### Post by cygnis1 on 2007-11-16
I know that it is a text file.  I am using konsole.  My question is what command do I use to open it?
Cygnis1

---

### Post by maybeway36 on 2007-11-16
```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by mellowd on 2007-11-16
```
vi /etc/X11/xorg.conf
```

or install vim and then 
```
vim /etc/X11/xorg.conf
```

---

### Post by cygnis1 on 2007-11-16
I am unable to edit the xorg.conf file.  How do I do that?

---

### Post by ruibernardo on 2007-11-16
Gnome version of maybeway36 post:

```
gksudo gedit /etc/X11/xorg.conf
```Without any desktop environment (can happen if you get no X for some reason after you edited it):

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by OffAxis on 2007-11-16
don't forget to restart the x-server after you've made the changes.
**Control+Alt+Backspace**

and if things have gone horribly awry and you've just got a command prompt
```
startx
```

---

### Post by mellowd on 2007-11-16
> **cygnis1 said:**
> I am unable to edit the xorg.conf file.  How do I do that?

Are you getting some sort of error or what is happening?

---

### Post by ruibernardo on 2007-11-16
Hi mellowd, 

cygnis1 wanted to edit his xorg.conf file because:
> **cygnis1 said:**
> I need to add the option "SHM Config" to on in the
touchpad section of /etc/X11/xorg.conf .  How do I do this?  how do I open the config file?

---

### Post by mellowd on 2007-11-16
Hi epimeteo.

yeah i know why he originally needed to edit the file but I'm wondering why he said this:

> I am unable to edit the xorg.conf file. How do I do that?

---

### Post by ruibernardo on 2007-11-16
Sorry, thought you didn't saw the first post, but it was me that didn't see what you were really asking. #-o

About the question: I would like to know that too, just posted guessing it would help somehow, but got no feedback since then...

---

### Post by mellowd on 2007-11-16
It's a bit odd because after 2 of us showed him examples of how to edit the .conf file he asked how to edit it?

---

### Post by ruibernardo on 2007-11-16
What I think that could have happen is that he/she didn't have KDE and found vi(m) to hard to use.

---

### Post by cygnis1 on 2007-11-17
Thanks everyone!  It worked.  I just crossed my fingers and put in the line to turn on the touchpad configuration tool,rebooted and it worked and my machine was not screwed up.  Much thanks.
Cygnis1

---

### Post by mellowd on 2007-11-17
good to hear :)

---

### Post by erfahren on 2007-11-17
> **cygnis1 said:**
> Thanks everyone!  It worked.  I just crossed my fingers and put in the line to turn on the touchpad configuration tool,rebooted and it worked and my machine was not screwed up.  Much thanks.
Cygnis1
just for info

the edit you made was a minor one but in the future when you go to edit system config files it's a good idea to back them up first
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back

```
 (or whatever)

then if needed you can restore the backup in recovery mode (by the comand line). I've had to do it a few times. You can also use nano from the command line to edit them if needed.

to reboot you type 
shutdown -r now

---

### Post by cygnis1 on 2007-11-17
Thank you.
Cygnis1

---


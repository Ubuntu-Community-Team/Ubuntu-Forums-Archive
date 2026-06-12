---
title: "Backup of sudo gedit /etc/X11/xorg.conf"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by jmattos on 2007-03-10
Hi there

I need to edit my sudo gedit /etc/X11/xorg.conf file as a part of setting up my ATI Radeon x1800 video card.

Before I change it, I want to back up.

What's the command to do that?

Thanks!

---

### Post by Kateikyoushi on 2007-03-10
For example.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck
```

---

### Post by Perfect Storm on 2007-03-10
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_BACKUP
```


reversing:
```
sudo cp /etc/X11/xorg.conf_BACKUP /etc/X11/xorg.conf
```

---

### Post by russell.h on 2007-03-10
And just so you know, its not a "sudo gedit /etc/X11/xorg.conf" file.

What you are doing when you type that in is first running "sudo" which gives the next command root access (in other words it gives it permission to modify /etc/X11/xorg.conf), then you are running "gedit" which is the text editor, and telling it to open "/etc/X11/xorg.conf".

Hope that made sense. Good Luck!

Russell

---

### Post by Kateikyoushi on 2007-03-10
You can read more about sudo gksudo here. [LINK]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by taurus on 2007-03-10
Please try not to use sudo with gedit.  If you want to use sudo, then use it with nano and if you want to use gedit, then use it with gksudo.

```
sudo nano -Bw /etc/X11/xorg.conf
```
or
```
gksudo gedit /etc/X11/xorg.conf
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jmattos on 2007-03-10
> **russell.h said:**
> And just so you know, its not a "sudo gedit /etc/X11/xorg.conf" file.

What you are doing when you type that in is first running "sudo" which gives the next command root access (in other words it gives it permission to modify /etc/X11/xorg.conf), then you are running "gedit" which is the text editor, and telling it to open "/etc/X11/xorg.conf".

Hope that made sense. Good Luck!

Russell

Right you are. I feel a little silly about that one. I meant to edit that before submitting

:-D

thank you all! Best support system EVER!!!!!!!

---

### Post by jmattos on 2007-03-10
> **taurus said:**
> Please try not to use sudo with gedit.  If you want to use sudo, then use it with nano and if you want to use gedit, then use it with gksudo.

```
sudo nano -Bw /etc/X11/xorg.conf
```
or
```
gksudo gedit /etc/X11/xorg.conf
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Good tip. Why is that?

---

### Post by russell.h on 2007-03-10
My understanding is that when you run a program with "sudo" you are running the program with root priveleges, but it uses the configuration files specific to you as a user (not root's configuration files). When this happens a program may write a configuration file, but since the program is being run as root it will give that file root permissions. Then the next time you run the program not as root the program won't be able to access the configuration files.

On the other hand when you use gksudo it uses root's configuration files *and* runs the program as root so you don't have that problem.

At least thats my understanding :) 

Russell

---


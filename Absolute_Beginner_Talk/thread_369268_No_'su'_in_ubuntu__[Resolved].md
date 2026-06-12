---
title: "No 'su' in ubuntu ? [Resolved]"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by elmerfud on 2007-02-24
I know nothing about Ubuntu.  I'm thinking of switching to it.  I've used RH/Fedora since RH8.

I understand that Ubuntu doesn't have the su command.   I use it every day.   I open a console, type 'su' and go to work on various things.   How does one run without su ?

And why isn't it in Ubuntu ?

Thanks

---

### Post by v8YKxgHe on 2007-02-24
Ubuntu uses "sudo" by default as it's suppose to be more secure (as you're not logged in as root all the time ... well, in the terminal if you do "su"). If you want to edit a file for example, with root privilege's you would do:

```
sudo gedit /etc/X11/xorg.conf
```

Sudo asks for you're users password, not 'roots' password.

---

### Post by taurus on 2007-02-24
> **AlexC_ said:**
> 
```
sudo gedit /etc/X11/xorg.conf
```


```
**gksudo** gedit /etc/X11/xorg.conf
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by highneko on 2007-02-24
There's a hidden su command kinda. It doesn't get mentioned much because sudo should be used instead.
```
sudo su
```

---

### Post by v8YKxgHe on 2007-02-24
> **taurus said:**
> ```
**gksudo** gedit /etc/X11/xorg.conf
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Old habit :) Hard to break when you've been doing "sudo" for around an year.

---

### Post by elmerfud on 2007-02-24
what is gksudo ?

Does Ubuntu have Konsole ? (KDE console)

Does sudo su allow me to be su in a terminal ?

Thanks for the quick answers.

---

### Post by aysiu on 2007-02-24
> **highneko said:**
> There's a hidden su command kinda. It doesn't get mentioned much because sudo should be used instead.
```
sudo su
```
There are a couple of hidden ones, actually: ```
sudo -s
``` and ```
sudo -i
```

---

### Post by aysiu on 2007-02-24
> **elmerfud said:**
> what is gksudo ? It's for graphical GTK apps. *kdesu* is for graphical QT apps. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> Does Ubuntu have Konsole ? (KDE console) It doesn't default to one, but Kubuntu does. Ubuntu's default terminal is *gnome-terminal*, but you can install *konsole* if you prefer that program: ```
sudo apt-get update && sudo apt-get install konsole
```

> Does sudo su allow me to be su in a terminal ? Yes, and so do a couple of other commands (as I mentioned in my last post).

---

### Post by elmerfud on 2007-02-24
Thank you.

---


---
title: "Skype Install"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-05-18
Hi, Im pretty new to linux in general, and have downloaded Skype. I want to install it now, I have three files extracted from an archive. The files are as follows:

data.tar.gz
debian-binary
control.tar.gz

What do I need to do with these files?
I have come from Windows XP, with my knowledge of computers I would assume clicking on the binary but that opens up Gedit and displays '2.0'.

Someone please help me?

Thanks very much, Tom

---

### Post by linuxcity on 2006-05-18
I haven't tried to install it manually, but it works when you use EasyUbuntu:

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

### Post by zerhacke on 2006-05-18
There's an easier way to install Skype.

Go to the following link - [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) .  SAVE the package to your home folder.

Open a terminal.  Type the following into your terminal.

```
dpkg -i skype_1.2.0.18-2_i386.deb
```

You should have skype installed then.

*or, do as Linuxcity suggest.

---

### Post by Klaidas on 2006-05-18
Here's a guide on ubuntu wiki: [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)
It's easy to install it now, as there is a ready-to-install deb file. Some time ago, you had to use "alien" and convert to deb from rpm :)

---

### Post by S{yndrom}e on 2006-05-18
Or just use arnieboy's script automatix

[http://ubuntuforums.org/showthread.php?t=138405]("http://ubuntuforums.org/showthread.php?t=138405")
Lots of other goodies that install without all that hassle of dpkging and the rest

---

### Post by patrick295767 on 2006-05-18
in my multimedia.sh script, there is also automatic skype installation ..; 
  
Greetz

---

### Post by enrique_setup on 2006-12-09
I've looked arround , and certainly this is the best procedure to install it. Thanks a lot

Enrique - Brazil

> **zerhacke said:**
> There's an easier way to install Skype.

Go to the following link - [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) .  SAVE the package to your home folder.

Open a terminal.  Type the following into your terminal.

```
dpkg -i skype_1.2.0.18-2_i386.deb
```

You should have skype installed then.

*or, do as Linuxcity suggest.

---


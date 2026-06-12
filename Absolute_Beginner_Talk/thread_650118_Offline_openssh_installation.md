---
title: "Offline openssh installation"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-12-25
i want to install openssh-server on my gutsy gibbon, but i couldnt find the deb file. i tried the rpm file from my rhel5 cds, but it didn't worked. any link?

---

### Post by jimrz on 2007-12-25
EDIT: oops you said offline. You can download from [[COLOR="Sienna"]**_this_**[/COLOR]]("http://packages.ubuntu.com/gutsy/net/openssh-server") site and then do the old sneaker net thing to get it to the box you want to install to.

---

### Post by shoaibi on 2007-12-25
hmmm missed the thread subject? :P

---

### Post by kd7swh on 2007-12-25
you can download the deb files from

[http://packages.ubuntu.com](http://packages.ubuntu.com) 

on a computer with the internet and burn them to a cd or put them on a usb drive.


[http://packages.ubuntu.com/gutsy/net/openssh-server](http://packages.ubuntu.com/gutsy/net/openssh-server)

---

### Post by JoshuaRL on 2007-12-25
Probably your best option is to go on another computer that has internet access and put the .deb onto the removable media of your choice.

[http://packages.debian.org/openssh-server](http://packages.debian.org/openssh-server)

That's debian but it should work.  Ubuntu 7.10 is based off of etch.

Not sure if there's another way besides that and apt-get.  But I may be wrong.

---

### Post by JoshuaRL on 2007-12-25
Aw man, beat me to it.  And you used ubuntu packages too.  Oops.

---

### Post by kd7swh on 2007-12-25
No problem, on the double post there. I wouldn't recommend using a debian package unless you have too (if the ubuntu package doesn't work). 

you could also do something like (on a networked ubuntu box):

```
sudo apt-get install openssh-server -d
```

the "-d" is download only it would download the deb to "/var/cache/apt/archives"

you could burn it to disk from there as well.

---


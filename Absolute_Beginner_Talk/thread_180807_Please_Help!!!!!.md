---
title: "Please Help!!!!!"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by phantomreaper on 2006-05-23
Hi, I know I might sound like a newbie by asking this, but 
I need help with this.

This is my delemmia.

I have no internet connection at home, and I have to go to my town's public library to use an internet connection, and I was wondering, with how it says to download packages which arent on the installation CD eg. Universe, restricted and security, and multiverse packages, is it possible to download all the packages I need to use from the library and then install them at home, because I've been having hell trying to install packages at home. 
Also I need to disable read-only parameters on my root directory, how can I do that?

---

### Post by Sef on 2006-05-23
> is it possible to download all the packages I need to use from the library and then install them at home, because I've been having hell trying to install packages at home.

For packages to download and then burn to a CD:

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by aysiu on 2006-05-23
Pop a Ubuntu live CD into the library computer.

Open a terminal and type: ```
sudo apt-get clean
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo cp breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install *nameofprogram1* *nameofprogram2* *nameofprogram3*
gksudo nautilus
``` Go to the /var/cache/apt/archives directory and copy the .deb files to something (a USB key, for example).

Then copy those .deb files to the desktop of your Ubuntu computer at home and paste these commands: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by K.Mandla on 2006-05-23
I can sympathize with you on this one. I have tried to install stuff on machines without Internet connections, and it's a real trick. One package relies on another, which relies on two others, and all those rely on still more. It's a real headache.

This might be of some help. ...

[http://www.ubuntuforums.org/showthread.php?t=136955](http://www.ubuntuforums.org/showthread.php?t=136955)

Aside from that, you might try this idea ...

[http://www.ubuntuforums.org/showthread.php?t=101790](http://www.ubuntuforums.org/showthread.php?t=101790)

... but that's quite a bit more complicated. 

Good luck!

EDIT: Aysiu's idea is probably better.

---

### Post by nanotube on 2006-05-23
[QUOTE=aysiu]Pop a Ubuntu live CD into the library computer.

Open a terminal and type: ```
sudo apt-get clean
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo cp breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install *nameofprogram1* *nameofprogram2* *nameofprogram3*
gksudo nautilus
``` Go to the /var/cache/apt/archives directory and copy the .deb files to something (a USB key, for example).

Then copy those .deb files to the desktop of your Ubuntu computer at home and paste these commands: ```
cd ~/Desktop
sudo dpkg -i *.deb
```[/QUOTE]
hehe, excellent idea, aysiu!

---

### Post by phantomreaper on 2006-05-23
Thank you for your help, I really appreciate knowing that there are others out there with the same problems as me. :-D

---

### Post by phantomreaper on 2006-05-23
Also I would like to know ummm..... what is the "executable" in linux

because I downloaded a game which wouldnt install because the root wasnt writable so I installed it into my home directory and I dont know what do to, how do I run it, I know I sound soooo stupid but I havent full on used Linux for a t least 4 years.

---

### Post by aysiu on 2006-05-23
Read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---


---
title: "Bypass apt's prompt for cd"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by kelbizzle on 2007-03-17
I wanted to know if there was a way to get past the prompt for the edgy cd when installing software via apt-get.

---

### Post by sad_iq on 2007-03-17
Type sudo nano /etc/apt/sources.list and put a # in front of the line about the cd (I think it's the first...but I don't remember corectly)

---

### Post by kelbizzle on 2007-03-17
thanks. I dunno if it did it. I ran into the issue installing openssh on a machine here and had to get up  and go do it. I didn't want to run into the issue again. Know any software I can install that requires a cd? I think apache2 does.

---

### Post by sad_iq on 2007-03-17
...forgot...you did do a **sudo apt-get update** after modifying** /etc/apt/sources.list** right? and I have never used the cd to install anything in ubuntu(it may contain old packages)...that's why I don't remember the line about the cd repo.
 And I don't think apache2 needs a cd to install!

---

### Post by aysiu on 2007-03-17
As long as you have a working internet connection, none of the software *requires* a CD.

As sad_iq points out, all you have to do is tell the package manager that the CD is no longer a source, and it will use the online repositories as sources instead.

Type ```
sudo nano -B /etc/apt/sources.list
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal). This will allow you to edit your sources.list while also making a backup copy of the old one.

You should see a whole bunch of sources in there. A # sign at the beginning of the line tells the package manager reading the file "Ignore this line." For example, this is the line "commented out" (meaning "Ignore this line"): ```
#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
``` And this is the line uncommented (meaning "Read this as a source for software installation"): ```
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
``` You want the CD line to be *commented* out (put the # sign in front of it).

But you want any line that looks like a web address to be *un*commented--lines that look like these: ```
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted
``` Then, to save, press Control-X, Y, then Enter.

To have the changes be recognized by the package manager, type ```
sudo apt-get update
``` Then you can install Apache 2 with this command: ```
sudo apt-get install apache2
``` If the CD source has a # in front of it and the online sources do **not** have # in front of them, the package manager should install from the online repositories and no longer prompt you for the CD.

---


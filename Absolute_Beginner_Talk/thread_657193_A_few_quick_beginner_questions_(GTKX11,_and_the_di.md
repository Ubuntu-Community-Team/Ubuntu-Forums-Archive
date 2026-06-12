---
title: "A few quick beginner questions (GTK/X11, and the different DEs)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by raptir on 2008-01-03
I'm not a complete beginner, but I'm close. I recently put Xubuntu on my old laptop (since I think it would have struggled to run the Gnome Desktop Environment), but I had a couple questions about what programs to use on it. Trying to install Emacs, for example, gives me two options: X11 or GTK. Which should I be using on my computer? I saw that most of the programs that come with Xubuntu are GTK+ 2, but I thought that X11 programs were supposed to be a little lighter (I could be completely wrong, tell me if I am). Bottom line though, should I use X11 or GTK when given the choice for a program?

Also, There are a few programs that I want to use that say that they require Gnome or KDE, such as Gnomad for my Creative MP3 player. Is there a way to install the framework for Gnome/KDE without installing the entire desktop environment plus all the additional applications that come with trying to install the Ubuntu or Kubuntu desktops?

Thanks in advance.

---

### Post by p_quarles on 2008-01-03
X11 vs. GTK: The first is a very minimal toolkit, whereas the latter will look more like other programs on your system. It comes down to personal preference, and both will work.

And, yes, you can use most Gnome and KDE programs. Any libraries or toolkits needed for their use will be automatically installed as dependencies (assuming that you're using the package manager).

---

### Post by raptir on 2008-01-03
Awesome, thank you. One more question though. I was trying to install Amarok, and it says it needs the Xubuntu install disk to install it. Is there anyway around that (I don't have the disk with me) or another good media player for ripping Mp3s? Thanks again.

---

### Post by p_quarles on 2008-01-03
Yeah, you just need to remove the install disk from your repository list. You can do that by entering the following command in the terminal:
```
gksudo mousepad /etc/apt/sources.list
```At the top of this file, you'll see a couple lines beginning with "deb cdrom:{etc.}". Place a "#" sign at the beginning of both of these lines (this disables those lines). Now, update the cache:
```
sudo apt-get update
```You'll now be able to install Amarok and anything else by simply downloading it.

---

### Post by ~LoKe on 2008-01-03
> **raptir said:**
> Awesome, thank you. One more question though. I was trying to install Amarok, and it says it needs the Xubuntu install disk to install it. Is there anyway around that (I don't have the disk with me) or another good media player for ripping Mp3s? Thanks again.

Do you still have the cd repository enabled in /etc/apt/sources.list?

If so, do this:
```
gksu gedit /etc/apt/sources.list
```
And put a # in front of the line that mentions the CD.

**EDIT**: p_quarles is a machine.

---

### Post by raptir on 2008-01-03
Great, thanks. Much easier to deal with now.

---

### Post by p_quarles on 2008-01-03
> **~LoKe said:**
> **EDIT**: p_quarles is a machine.
:guitar:

---


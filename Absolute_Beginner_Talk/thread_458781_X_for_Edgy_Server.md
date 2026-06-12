---
title: "X for Edgy Server"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by NeedX on 2007-05-30
Hi,

I have seen similar posts, but the advice tendered didn't seem to help.  I installed Ubuntu Server Edgy version and found that it doesn't seem to come preinstalled with a GUI.  I am getting tired of typing 'ls' over and over so I would like to install X.

There are X directories under /etc  in place but it seems to be an incomplete installation.  Below are commands I have tried that come back 'library not found' or something similar:

sudo apt-get install xserver-xorg
apt-cache search xserver
sudo apt-get install gnome-desktop
sudo aptitude install x-window-system-core gnome gdm
sudo dpkg-reconfigure xserver-xfree86
apt-get install gdm
sudo aptitude install kubutu-desktop

I obviously have no idea what the hell I am doing.  I can't find anything to install if I just browse around inside aptitude.  I want to keep the server version because I want to set up an apache server but I like using a mouse too.  All of this Bash wandering has been helpful in learning a bit of Linux syntax but the sight of the monochrome screen is making me sick.  I served my time with DOS.

Any advice you can give would be appreciated.

---

### Post by zvacet on 2007-05-30
If you want GNOME

```
sudo aptitude install ubuntu-desktop
```

and for KDE 

```
sudo aptitude install kubuntu-desktop
```

---

### Post by NeedX on 2007-05-30
It says "couldn't find any package whose name or description matches  ubuntu-desktop". same for kubuntu-desktop.  Do I have an incomplete distribution?

---

### Post by Outrunner on 2007-05-30
Is the internet working?

```
sudo ping -c 3 bbc.co.uk
```

---

### Post by NeedX on 2007-05-30
Yeah, internet is fine.  Aptitude is a local process tho, right?

---

### Post by NeedX on 2007-05-30
At this point I am sure that my distro CD does not have a desktop on it.  I reinstalled the whole damn thing and the only options I had were to install LAMP and DNS.  If I want a desktop I need to download it.  Is there any way I can do that?

I tried downloading the newest copy of X from x.org, but that just had a bunch of .c files that I have no idea how to compile.  Their documentation sucks.  If anyone knows how to do this I would appreciate it.

---


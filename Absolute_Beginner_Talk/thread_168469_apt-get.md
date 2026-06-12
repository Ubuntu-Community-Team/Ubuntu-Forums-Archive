---
title: "apt-get"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by ddavid123 on 2006-04-30
I wanted to install Wine using synaptic yesterday, but the Wine version was 0.2 or something, but I wanted to install 0.9.12.  So I went to the command line and typed "apt-get update wine", but I recieved an error saying apt couldn't lock on to a certain file.  I thought I may have to be root to do this so I typed "su".  It then asked me for the "root" password, but I don't know it.  I wasn't given the option to enter a root password when I installed Ubuntu.  What do I do to find the root password?  Also, I entered the apt line in synaptic like the Wine download for Ubuntu said.  I went to settings, then repositories, then added the Wine apt line "deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/" and "deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/".  But when synaptic updated the repositoties, many of the files would not load for wine!  So I am left with Wine 0.2, If I could log in as root, I could update but I can not

Please help me and any help is greatly appreciated!

---

### Post by lukem on 2006-04-30
Ubuntu does not use a separate password for root.  If you installed Ubuntu then your password is the password being requested when you su.

Good Luck & Have Fun

---

### Post by nalmeth on 2006-04-30
you can't:
sudo apt-get update an_app

first, just go straight:
sudo apt-get update
sudo apt-get upgrade

if you can find a .deb for the newest wine (not in repositories yet) you can install it with:
sudo dpkg -i wine????.deb

---

### Post by TheTux on 2006-04-30
maybe u can try this..sudo passwd...then enter new root password

---

### Post by Iandefor on 2006-04-30
[quote=TheTux]maybe u can try this..sudo passwd...then enter new root password[/quote] See how well that works when they try to login via GDM ;).
If you want to be able to use X while root, you also need to enable logging in as root via the GDM configuration dialog. I believe it's under the Administration menu. In the dialog itself, the option should be under "Security". Then again, it's recommended that you use sudo. It tends to be more secure.

---


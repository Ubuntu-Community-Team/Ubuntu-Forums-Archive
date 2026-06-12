---
title: "Yahoo n msn messenger"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Cool Surfer on 2006-11-07
I am running ubuntu 6.1.0, but yahoo n msn messenger are not working.
Thanks.

---

### Post by zvezdogled on 2006-11-07
what about  gaim internet messenger
with it you can use both msn and yahoo

---

### Post by d3v1ant_0n3 on 2006-11-07
Give GAIM a try. You can sign into your yahoo/MSN/AIM/etc accounts, and do most of the things you can usually do.

---

### Post by chocbar31 on 2006-11-07
Yahoo...that crappy 50 year-old version. C'mon, you don't want that...LOL At least for the linux version anyways. Yahoo, has some major upgrading to do with their version of the IM client for Linux.

I am not really an MSN person; however, if you like Yahoo like I do, then use Gyach. It excellent privacy and security features. You can even see when people are trying to be invisible...I love this feature. "You can rung; but you can't hide" LOL

Anyways, if you're up for trying Gyach; not to mention video send/receive is pretty much native in Gyach. There are some draw-backs to Gyach, but not enough to even select the Yahoo's messenger client over Gyach...even if I was running the .CRASH OS!


1. Download [http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2]("http://www.politicalcrossfire.com/temp/enderavsig/gyach-install.tar.bz2") , and save it to your home directory (important!).

2. Run these commands in the terminal, in sequential order:
Code:

tar -xjf gyach-install.tar.bz2
cd gyach
sudo ./install

Gyach:

[http://www.phrozensmoke.com/projects/pyvoicechat/]("http://www.phrozensmoke.com/projects/pyvoicechat/")

---

### Post by Cool Surfer on 2006-11-07
I tried gaim, its not working. Dunno why. I have used it before.
ANy idea what port no's are recomemnded?

---

### Post by Cool Surfer on 2006-11-07
When I type su, it asks me for a password. I enter the password, but it says authentication failure. Is there some default password for root?

---

### Post by chocbar31 on 2006-11-07
Don't type su...rather type sudo or gksudo

Example:
sudo apt-get update
sudo apt-get install
sudo gaim     [B]but don't advise running gaim as root
[/B]
It should run from the menu, from the internet section. If it is not installed, then use either Synaptic, Add/Remove, or Automatix to install it.

Code:

sudo aptitude install gaim
or
sudo apt-get install gaim

When it asks for a password, this will be your password.

---

### Post by Cool Surfer on 2006-11-08
I get this error
=============
r: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tar: /gyach_enhanced_fonts2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rmdir: /home/cool/gyach: No such file or directory
cool@cool-desktop:~/Desktop/gyach$ 
==================

Have to login into yahoo or msn, itternet is bland without yahoo n msn chat.

---

### Post by Sef on 2006-11-08
Another alternative is Kopete, which is KDE's messenger clone.  Also for msn, download aMSN.  It is in universe, so you have to have enabled that repository.

---

### Post by chocbar31 on 2006-11-09
Copy and paste this code into a terminal:

sudo apt-get install libasound2 libasound2-dev libasound2-plugins libatk1.0-0 libaudiofile0 libaudiofile-dev libesd-alsa0 libexpat1 libexpat1-dev libfreetype6 libfreetype6-dev gtk2-engines-pixbuf libgdk-pixbuf2 libglib2.0-0 libgtkhtml2-0 libltdl3 libltdl3-dev libpango1.0-0 libx11-6 libxext6 libxi6 libxml2 libxrender1 libgpgme6 libmcrypt4 mcrypt

and then install using the .deb method.

This should get you running, if you aren't yet!

Also, look at the page below. Do not attempt to get the deb file, as it does not work.

[http://www.ubuntuforums.org/showthread.php?t=177081](http://www.ubuntuforums.org/showthread.php?t=177081)

---


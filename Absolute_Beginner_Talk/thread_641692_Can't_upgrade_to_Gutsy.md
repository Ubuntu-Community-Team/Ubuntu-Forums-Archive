---
title: "Can't upgrade to Gutsy"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by loki233 on 2007-12-15
I am try to upgrade from Feisty to Gutsy, and found this command line on the internet:

gksu "update-manager -c "

I ran this, and it got me a bunch of updates and then said the Gutsy upgrade was available and so I clicked on it to download, and I think it downloaded, but nothing appears to have happened. I have restarted my system several times to no avail.  I am still running 7.04 and the message to let me download the upgrade is no longer present when I run the update manager.

---

### Post by taurus on 2007-12-15
First, make sure you don't have any 3rd party repos in your /etc/apt/sources.list because they could cause trouble when you try to upgrade from Feisty to Gutsy.  Then, look at this link for the official how.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by loki233 on 2007-12-15
I also just noticed that in the terminal, under where I typed in the line :

gksu "update-manager -c "

A line appeared that said:

warning: could not initiate dbus

---

### Post by loki233 on 2007-12-15
When I go to the Update Manager, the message that says an upgrade is available doesn't pop up.  However, I looked in the System Monitor and it still says im running 7.04.

---

### Post by loki233 on 2007-12-15
I don't know what this means, but I'm doing this from a fresh install.  I don't think I have any extra stuff, unless there is a problem with UbuntuStudio.  I installed UbuntuStudio through Wubi, if that makes any difference.

---

### Post by flamelab on 2007-12-15
I'd would propose you not to upgrade to a new version of Ubuntu "like this" .
The first thing is that when you have upgraded , half the system will still be ... Feisty .

Especially , you are going to have problems regarding the restricted drivers ( kernel update ) and Compiz Fusion ( 0.60 is incompatible to 0.52 even though they have few differences ).

The best thing is to back up your settings (/home , /opt, /var ) , and fresh install Gutsy :)

---

### Post by loki233 on 2007-12-15
I would just fresh-install Gutsy, but my simplest option to get this installed without messing with my vista install is using Wubi.

---


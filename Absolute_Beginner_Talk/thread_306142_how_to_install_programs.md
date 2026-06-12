---
title: "how to install programs"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by xonuxus on 2006-11-24
I managed to install Ubuntu on my PC and now I need a music player... I've been searching on google for xmms, I've downloaded it but I can't figure out how to install it... I don't understand how to install...](*,)

---

### Post by smile_sunshine on 2006-11-24
Hey,

probably an easier way is to open synaptic (click on applications its there). 
It will ask for a password, which is just the password you use to log in. 
you can search for xmms, mark it for installation and click apply to install it - synaptic should install for you automatically :) 

hope that helps

---

### Post by qamelian on 2006-11-24
> **xonuxus said:**
> I managed to install Ubuntu on my PC and now I need a music player... I've been searching on google for xmms, I've downloaded it but I can't figure out how to install it... I don't understand how to install...](*,)
Go to the Applications menu and select Accessories-->Terminal.
In the terminal window, type: ```
sudo aptitude install xmms
``` and press enter. This will install xmms from the Ubuntu repositories.

If you want to see what software is available from the repositories, go to the System menu and select Administration--->Synaptic Package Manager. When it asks for a password, provide your own. You can search for software in Synaptic or you can browse software by category.

---

### Post by SupremePiracy on 2006-11-24
Hey

Alright, first of all you need to add extra repositories. 

Backup your source list and then open it with gedit like this.
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

Then replace everything in your source list with this.
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen
```

Then use the following commands to download and install xmms.

```
sudo apt-get install xmms xmms-skins
wget -c http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
```

Note: you always use the "sudo apt-get install" command to get and install things, sudo is for root privileges.

Hope that will help.

---

### Post by dbott67 on 2006-11-24
Here's a nice graphic tutorial:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

or our own aysui's spot on the web:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

-Dave

---

### Post by aysiu on 2006-11-24
If you don't want to use the terminal, read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by turbojugend_gr on 2006-11-24
M8, from what I understand you have clearly not understand how it works Linux wise.

Here is the preferable way to install an app. (btw xmms look like winamp 2 years ago, try Listen if you like iTunes, or Rhythmbox which is already in your pc by default)

1. You open add/remove Programs: Application>>Add/remove programs, usually the last choice on that menu. You search there for some very common apps. Preferably used when you don't know what you need to install.

2. Open Synaptic: Accessories>>Admin>>Synaptic Package Manager. It's the whole deal to add/remove programms, and the gui interface to the command line tools aptitude/apt-get. You search with various keywords, for name/name-description etc. When you find a desired app, check it to install, apply, you are done.

Before continuing I understand I would better give you some guides to get your self familiar with your new OS.

1. Official [Ubuntu Desktop Guide]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html").
2. [Ubuntuguide.org's guide]("http://www.ubuntuguide.org")
3. [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")
4. Some great how-to's/guides from asyiu, on [psychocats]("http://www.psychocats.net/ubuntu/index.php")


Read 'em as much as you like, preferably in that order. You will find almost everything you need there to get familiar with ubuntu, installing apps in ubuntu is well covered in the guides, so go for it.

PLZ read 'em, as I keep encouraging users to save time, and somehow the think it is a hore to read, the ubuntu desktop guide for instance, has everything categorized so you can go to installing a music player or sth, and then read the other stuff, if you are impatient. Follow this piece of advice and I am sure you won't regret it. ;)

Best Regards, TJ.

---

### Post by xonuxus on 2006-11-24
Ok... now i got it... thank you very much... :)

---


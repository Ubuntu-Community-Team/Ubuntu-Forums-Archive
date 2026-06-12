---
title: "Yahoo Messenger"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by mholl26 on 2007-12-21
Can someone give me a step by step help on how to make Yahoo Messenger work with Ubuntu.

Thanks for your help and time.

---

### Post by doorknob60 on 2007-12-21
Programs like Pigdin (comes preinstalled with Ubuntu) can connect to Yahoo Messenger :D You can find it in your applications menu.

---

### Post by mholl26 on 2007-12-21
I couldn't find pidgin in the apps menu so I tried to install it through Synaptic and got this message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by doorknob60 on 2007-12-21
I've had that error a few times before, but its easy to fix. Simply open a terminal in and type in ```
sudo dpkg --configure -a
``` and it should be fixed in no time. Also, it might be called Gaim instead of Pidgin.

---

### Post by mholl26 on 2007-12-21
Pardon my newness.  How do I open a terminal?

---

### Post by doorknob60 on 2007-12-21
Click applications, go to accesories, and click on terminal.

---

### Post by _angel__ on 2007-12-22
I heard that yahelite's working through WINE, but i couldn't get voice. and I don't like pidgin. So I just run yahoo messenger and windows live messenger in virtualbox, both work perfectly.

---

### Post by doorknob60 on 2007-12-22
> **_angel__ said:**
> I heard that yahelite's working through WINE, but i couldn't get voice. and I don't like pidgin. So I just run yahoo messenger and windows live messenger in virtualbox, both work perfectly.

I don't think it's worth it to use VirtualBox for IMing...but if it worked in WINE that would be an option.

---

### Post by spiderbatdad on 2007-12-22
gyache is awesome and has a deb package.

---

### Post by Steve Zenone on 2007-12-22
If you're still having problems finding/installing Pidgin after doing dpkg, I recommend the following (more so as a sanity check):

1. Add the following to your /etc/apt/sources.list (I'll assume you're running Gutsy):
[INDENT] deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse
 deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse[/INDENT]
To do this pull up a terminal (APPLICATIONS | ACCESSORIES | TERMINAL). Then type:
[INDENT]  sudo cp /etc/apt/sources.list /etc/apt/sources.list.BAK
  sudo gedit /etc/apt/sources.list[/INDENT]
Copy and paste the deb and deb-src lines above to the end of your *sources.list* file. Save.

2. Get the GPG key. While in the terminal window type:
[INDENT]wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt) -O- | sudo apt-key add -[/INDENT]
3. Do the update and install. Again still in your terminal window type:
[INDENT]sudo aptitude update
sudo aptitude install pidgin
sudo aptitude install pidgin-libnotify[/INDENT]
4. You will find Pidgin in APPLICATIONS | INTERNET | PIDGIN INTERNET MESSENGER.

---


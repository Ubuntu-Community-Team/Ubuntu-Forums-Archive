---
title: "How do you uninstall kiba dock?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Fleece Flamingo on 2008-01-03
I used [this thread]("http://ubuntuforums.org/showthread.php?t=554127") to install it but I could never get it to work configure properly so I need to uninstall it from the terminal.

---

### Post by SOULRiDER on 2008-01-03
If you couldnt get past the 
```
./configure
``` part dont worry, just delete the directory containing all the files.

---

### Post by Fleece Flamingo on 2008-01-03
No lol by configure I mean, that I couldnt get it to work. I have completed all steps and when I try ```
cd kiba-dock/kiba-dbus-plugins
sudo make uninstall
cd ..
``` I get

```
make: *** No rule to make target `uninstall'.  Stop.

```

---

### Post by Lostincyberspace on 2008-01-03
Try using apt-get it might do something.

---

### Post by Fleece Flamingo on 2008-01-03
Like apt-get kiba-dock? That wont do anything. And besides, I want to uninstall it.

---

### Post by Lostincyberspace on 2008-01-03
More like ```
apt-get uninstall kiba-dock
```

---

### Post by Fleece Flamingo on 2008-01-03
Nope I get ```
E: Invalid operation uninstall
``` thanks for the suggestion tho! :)

---

### Post by LookTJ on 2008-01-03
> **Fleece Flamingo said:**
> Nope I get ```
E: Invalid operation uninstall
``` thanks for the suggestion tho! :)
apt-get remove

---

### Post by Lostincyberspace on 2008-01-03
Sorry I don't remove with apt-get i use synaptic. But it probably wont work any way.

---

### Post by Fleece Flamingo on 2008-01-03
```
pj@pj-desktop:~$ apt-get remove kiba-dock
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
pj@pj-desktop:~$ sudo apt-get remove kiba-dock
[sudo] password for pj:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-dock
pj@pj-desktop:~$ 

``` Nope, just a note to you guys. I never got kiba dock working so can I still uninstall it or will it be complicated?

---

### Post by LookTJ on 2008-01-03
> **Fleece Flamingo said:**
> ```
pj@pj-desktop:~$ apt-get remove kiba-dock
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
pj@pj-desktop:~$ sudo apt-get remove kiba-dock
[sudo] password for pj:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-dock
pj@pj-desktop:~$ 

``` Nope, just a note to you guys. I never got kiba dock working so can I still uninstall it or will it be complicated?
Make sure you read what it says ;). It asked if you were root. So you have to be superpower user to type that command.

> sudo apt-get remove kiba-dock

But, if that fails, I'll leave it to someone smarter than me, like laroza:)

---

### Post by Fleece Flamingo on 2008-01-03
I did,it was in that code it still didnt work tho. You guys are atleast 1,000 times smarter than me :lolflag:

---

### Post by Lostincyberspace on 2008-01-04
If doesn't do any thing just leave it or delete the code and move one.

---

### Post by cwgannon on 2008-01-31
Not sure if you're currently working on this, but...

See the post at: [http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127") for uninstallation instructions.

Just run all the "sudo make uninstall"'s listed at the bottom of the first post there.  If they do their job, it's uninstalled.  If they don't, it was never really installed, so you can just delete all the files and be on your way.

(If none of the above appeals to you, why not try a reinstall and then an uninstall?)

---


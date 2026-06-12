---
title: "How to change source of package with apt-get"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by Tee-Em on 2006-05-10
Hi,
installed Linux on old notebook and I am unable to install certain packages as the cd-drive is dodgey.  Battled on and am almost sorted. 
I need some help please so that instead of trying to install the missing packages from Cd I would like to force it to fetch it off one of the http sources. Internet sources working fine and have updated some packages from online sources.
Chrs

---

### Post by kaffeine on 2006-05-10
open /etc/apt/sources.list and comment out the first line (or two) that says 'deb ///cdrom/...'. since you said internet sources are working fine, an 'apt-get update' after this edit should get you an updated list of packages from the ubuntu online repo. any apt-get after this would not ask you to insert the CD for packages.

---

### Post by aysiu on 2006-05-10
There are several ways to approach this.

1. As mentioned above, you can edit the /etc/apt/sources.list by copying these commands into the terminal: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Then, put a # in front of a line to "comment it out" (essentially, you're deleting it). Put that # in front of the CD-ROM line, which is usually the first line. Then, Control-X (save), Y (confirm), Enter (exit).

2. Go to Synaptic Package Manager and go to Settings > Repositories and uncheck the box next to the CD-ROM source. I'm not sure if Adept has a similar function, but it probably does somewhere.

3. If you just want some extra repositories *and* the removal of your CD-ROM source, paste these commands into a terminal: ```
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list_old
sudo mv breezy.list /etc/apt/sources.list
```

---

### Post by Tee-Em on 2006-05-10
Thanks guys...
damn quick help around here... :)

---

### Post by Tee-Em on 2006-05-10
Thanks sorted... happily downloading as we speak..
Chrs for help.

---


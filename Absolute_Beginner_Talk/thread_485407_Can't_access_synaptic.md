---
title: "Can't access synaptic"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-06-26
My computer did one of those shutdowns by itself. Upon restart synaptic won't open and software updates has updates to install but can't. How do I get synaptic to run again?

---

### Post by charles.g.moore on 2007-06-26
> **captgadget said:**
> My computer did one of those shutdowns by itself. Upon restart synaptic won't open and software updates has updates to install but can't. How do I get synaptic to run again?

You could try this:

start up a terminal session alt-f2 then type gnome-terminal

type:
sudo aptitude update
sudo aptitude dist-upgrade

those 2 commands will get you updated, and hopefully fix your synaptic problem...

---

### Post by captgadget on 2007-06-26
won't work

---

### Post by charles.g.moore on 2007-06-26
> **captgadget said:**
> won't work


what wont work???

the dist upgrade part or the synaptic being fixed part?

what is the exact error message that you get?  cut and paste it from your command line into your post

---

### Post by captgadget on 2007-06-26
the sudo aptitude update worked

the sudo aptitude dist-upgrade returned this: captgadget@captgadget-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
captgadget@captgadget-desktop:~$

---

### Post by w4ett on 2007-06-26
Your package manager is broken....try this:

sudo dpkg --configure -a

sudo mv -f /var/lib/dpkg/status /var/lib/dpkg/status_backup

sudo mv -f /var/lib/dpkg/status-old /var/lib/dpkg/status

sudo apt-get update



If this doesn't work, a reinstall will be required

---

### Post by captgadget on 2007-06-26
sudo dpkg --configure -a I get this captgadget@captgadget-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 12 package `python-bittorrent':
 file details field `Size' not allowed in status file
captgadget@captgadget-desktop:~$

---

### Post by w4ett on 2007-06-26
Keep your fingers crossed...try this:

sudo cp -f /var/backups/dpkg.status.0 /var/lib/dpkg/status

sudo apt-get update

---

### Post by ububaba on 2007-06-27
> **charles.g.moore said:**
> You could try this:

start up a terminal session alt-f2 then type gnome-terminal

type:
sudo aptitude update
sudo aptitude dist-upgrade

those 2 commands will get you updated, and hopefully fix your synaptic problem...

My Archive Manager is not working properly. Does not recognize RAR or ZIP anymore. The attempts
at reinstalling are frustrated as I get stuck at 
[HTML]99% [Connecting to archive.ubuntu.com (91.189.88.31)]
[/HTML]

I tried 

```
sudo aptitude update
```

but that too in vain as it is impossible to connect. Any idea? Thanks.

---


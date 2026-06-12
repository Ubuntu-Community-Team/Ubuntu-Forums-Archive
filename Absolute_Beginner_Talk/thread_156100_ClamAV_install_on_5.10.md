---
title: "ClamAV install on 5.10"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by gymsmoke on 2006-04-06
Installing clamav on Breezy Badger - 

E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured

I tried to copy the terminal messages from the error dialog, but couldn't...
Anyone know if those messages are stored somewhere and where they would be?

---

### Post by dcstar on 2006-04-06
[QUOTE=gymsmoke]Installing clamav on Breezy Badger -

E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured

I tried to copy the terminal messages from the error dialog, but couldn't...
Anyone know if those messages are stored somewhere and where they would be?[/QUOTE]
You really need to note the dependencies.

If you are installing via Synaptic you should get these set to install as part of the process.

---

### Post by gymsmoke on 2006-04-06
The errors were displayed in a terminal window (as part of synaptic), but I couldn't select and copy the text from there.  Unless there is a place where the errors got recorded, I'm afraid I'm sol on getting them back, unless I un-install them and re-install them again, but, then how do I record the errors when they happen again?

---

### Post by dcstar on 2006-04-07
[QUOTE=gymsmoke]The errors were displayed in a terminal window (as part of synaptic), but I couldn't select and copy the text from there.  Unless there is a place where the errors got recorded, I'm afraid I'm sol on getting them back, unless I un-install them and re-install them again, but, then how do I record the errors when they happen again?[/QUOTE]
Try this in a terminal:
```
sudo apt-get install clamav-base
```

---

### Post by gymsmoke on 2006-04-07
Reading package lists... Done
Building dependency tree... Done
clamav-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by gymsmoke on 2006-04-07
I really can't believe I have to HAND TYPE this, but...
I did the same install on another fresh install of Ubuntu 5.10
.
.
.
Setting up clamav-base (0.87.1-1-breezy1)...
adding system user 'clamav'...
adding new group 'clamav' (114)
adding new user 'clamav' (114) with group 'clamav'
Not creating home directory
dpkg: error processing clamav-base (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
clanav-freshclam depends on clamav-base (= 0.87.1-1-breezy1); however: Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
dependency problems - leaving unconfigured.
dpkg: dependency problems prevent configuration of clamav:
Package clamav depends on clamav-freshclam | clamav-data; however:
Package clamav-freshclam is not configured yet.
Package clamav-freshclam is not configured yet.
Package clamav-data is not installed.
Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
dependency problems - leaving unconfigured.

The end result of this is - 
Errors were encountered while processing:
clamav-base, clamav-freshclam, clamav...
I'll try and manually step this through and see what happens. Maybe the dev team just has a broke installer script...

---

### Post by erniewinner on 2006-04-07
i dont mean to be rude by suggesting something easier but if you download the avast4workstation-1.0.4.tar.gz and unarchive it go to the bin folder and click "avast gui"... it works! although i think they want you to register. can't get easier than that. 8)

---

### Post by dcstar on 2006-04-07
[QUOTE=gymsmoke]Reading package lists... Done
Building dependency tree... Done
clamav-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/QUOTE]

Well, that means apt thinks that part is ok, try installing the rest through Synaptic now.

---

### Post by gymsmoke on 2006-04-08
David~
Thanks.  I did get clamav/freshclam to install ok.  Had to manually apt the pieces in place.

I looked up the link from the freshclam log regarding the version being outdated.  It is.  Do you  know if running this as an earlier version has any functional consequences?

---


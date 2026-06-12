---
title: "VMTOOLS and Ubuntu"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by mlhuzzy on 2007-09-13
Hi, I'm a complete novice and stuck at the first hurdle. Hoping you can solve this issue I have. Running Ubuntu 7.04 via VMWare, installs all fine and Ubuntu looks great but I can't install VMTOOLS. When I select 'INstall VM Tools' the process just sits there and doesn't do anything, no icons appear etc. I then follow further instructions but mounting my cdrom drive and trying to tar some files but the directory structure for VMTOOLS isn't on my CD....infact I can find anything on my Ubuntu CD that ididcates it has VM tools loaded on it. So, just wondering is there an easier way to install VMWare Tools with Ubuntu?
Thanks

---

### Post by mikeyphi on 2007-09-13
use Synaptic - search for 'vmware'  - it's in the repo's

---

### Post by Scotty562 on 2007-09-13
I'm in the same boat man, good luck on finding a solution. I'll be watching this thread.

---

### Post by benshead on 2007-09-14
Here's what worked for me:
[LIST=1]
[*]In VMWare Server, click <VM-->Removable Device-->CD-ROM...-->edit>
[*]Be sure device status 'connected' is selected and select 'use iso image'
[*]Browse to Your VMWare Server installation and find the 'linux.iso' file. Mine was at 'C:\Program Files\VMware\VMware Server\linux.iso'
[*]Click 'OK'
[*]Open a terminal in your host and ```
sudo mount /media/cdrom0
```
[*]Now you should be able to rejoin the instructions that you have been using. If you ```
ls /cdrom/
``` you will see the files you need.
[/LIST]

I hope this helps. I'm still stuck on finding a copy of vmware-tools-any-update*.tar.gz. Anyone found one?

---


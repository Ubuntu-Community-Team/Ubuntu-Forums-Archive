---
title: "Install Wine"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-30
Hello!
Sorry please tell me how to install Wine.
Thank you.

---

### Post by emarkd on 2008-01-30
Its in Synaptic.

---

### Post by alxlabs on 2008-01-30
Option 2: type in console 
```

sudo apt-get install wine

```

---

### Post by mikeyphi on 2008-01-30
> **Hoom@n said:**
> Hello!
Sorry please tell me how to install Wine.
Thank you.

Open System/Administration/Synaptic Packet Manager
Enter your password
select 'search' from top menu
enter 'wine' in search box - click on search
click on box next to wine
click on apply box - top menu

After install - Find wine icon on main menu.

---

### Post by Whiffle on 2008-01-30
I would suggest adding the repository from winehq, then reloading, and installing their version.  Its more up to date.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by b0rka7a on 2008-01-30
synaptic will install wine 0.9.46 :)
if you want to install the latest version (0.9.54) go here:
[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

---

### Post by Hoom@n on 2008-01-30
Thank you. I used ```
sudo apt-get install wine
``` Hope to work!

---

### Post by Hoom@n on 2008-01-30
And how can I install a windows program in wine?
Thank you.

---

### Post by mikeyphi on 2008-01-30
> **Hoom@n said:**
> And how can I install a windows program in wine?
Thank you.

Read here: [https://help.ubuntu.com/community/Wine?](https://help.ubuntu.com/community/Wine?)

---

### Post by b0rka7a on 2008-01-30
For example:
If you want to start setup.exe from the cdrom open a terminal and type:
```
wine /media/cdrom0/setup.exe
```
You may want to start winecfg and autodetect the drives.

*Edit: [Stuff I've learned about Wine](http://ubuntuforums.org/showthread.php?t=497332) *

---

### Post by Hoom@n on 2008-01-30
Thank you!

---


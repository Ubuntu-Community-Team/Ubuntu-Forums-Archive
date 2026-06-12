---
title: "GRUB dual boot 10 second timeout"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by CafeRay on 2007-03-28
I successfully installed UBUNTU (Edgy) on an XP desktop computer, and choose GRUB as the boot manager so that it would dual boot to either Windows or Linux.

GRUB was installed into the master boot record of the hard drive (replacing the NT Boot Manager) and LILO was installed into the root of the boot partition chosen for UBUNTU.

The problem I have is that the default settings for GRUB have a 10 second timeout before selecting UBUNTU to boot up.  This means I have to watch every second during bootup for the GRUB menu so that I can choose Windows.  I need to change the GRUB timeout to something much longer so I have a chance to choose which OS I want to boot.

---

### Post by freebird54 on 2007-03-28
Would not be a bad idea to backup the file first - just in case :)  Open a terminal and:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

All you need to do is specify how many seconds you want.  Use this command:

```
gksudo gedit /boot/grub/menu.lst
```

and modify the section that looks like this:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

```

to the value you want..

---

### Post by kittyhawk63 on 2007-03-28
.

---

### Post by DirtDawg on 2007-03-28
To do this, you need to edit the grub menu manually, but this is not hard.

First, make a copy of your current configuration (I use a '.bak' extension for backups)
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 
```

Next open the menu.lst file
```
 gksudo gedit /boot/grub/menu.lst 
```

Look for a section, probably near the top, that reads:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10 
```

As you can see, the 'timeout' is set to 10 seconds. Change that to whatever you would like, save,  and you're done!

P.S. While you're at it, I recommend finding the section that says:
```
# Pretty colours
#color cyan/blue white/blue 
```
and removing the '#' in the second line so it looks like:
```
# Pretty colours
color cyan/blue white/blue
```
There's no practical reason to do this, but it sure looks nice.

Hope this helps.

EDIT: Ha! Nearly verbatum response with freebird.

---

### Post by freebird54 on 2007-03-28
Yeah - I alternate that one with the one showing GrubEd for 'no touch' editing  :D

---


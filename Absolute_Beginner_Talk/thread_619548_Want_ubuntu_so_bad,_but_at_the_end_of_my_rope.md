---
title: "Want ubuntu so bad, but at the end of my rope"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Popbot on 2007-11-21
Hey all, thanks for looking

I have a MSI p965 Platinum (yes it is one of those problems, yes I have looked at/searched for other threads) and I absolutely cannot get Ubuntu 7.10 to recognize my SATA hard drive. 

My setup is a 80gig SATA drive with Vista on it, and a 250 gig IDE drive for storage and the like. I would like to install and boot Ubuntu from the SATA, but that isn't really a requirement. My problem is, since Ubuntu (and GRUB) wont see the SATA drive, I would have to switch the boot order in the BIOS to pick which OS to boot up.

So, I was wondering if:
1) There is someway to get Ubuntu to see my SATA drive
or
2) I can install Ubuntu on the IDE, and then somehow modify the Vista boot file to see Ubuntu so I can keep the SATA as my primary drive and not have to keep switching the boot orders.

Help!

---

### Post by celticbhoy on 2007-11-21
Might be simplistic, but if you install Ubuntu on the IDE, and then use the BIOS boot order option at startup it may give you an ugly but working fix ???

---

### Post by Popbot on 2007-11-21
Yah, I figured I could do that, but I would *really* prefer not to have to.

---

### Post by celticbhoy on 2007-11-21
Just to check, I take it you have run the live-cd, and you cant access the sata drive??

And if so, have you tried to start the install proccess to see if it is visable to the installer ??

---

### Post by Popbot on 2007-11-21
I've booted up the Live CD and started the install, it can only see the IDE drive. I have tried tweaking my BIOS, but still no luck.

---

### Post by celticbhoy on 2007-11-21
Did you go into manual setup, or ditch out when it offered guided ???

---

### Post by lespaul_rentals on 2007-11-21
Is it possible that Ubuntu can't see the drive because it's NTFS?

EDIT: Nevermind, stupid question.

---

### Post by celticbhoy on 2007-11-21
Shouldn't be an issue, as almost any other dual boot setup with XP or Vista will be NTFS.

---

### Post by stchman on 2007-11-21
> **Popbot said:**
> Hey all, thanks for looking

I have a MSI p965 Platinum (yes it is one of those problems, yes I have looked at/searched for other threads) and I absolutely cannot get Ubuntu 7.10 to recognize my SATA hard drive. 

My setup is a 80gig SATA drive with Vista on it, and a 250 gig IDE drive for storage and the like. I would like to install and boot Ubuntu from the SATA, but that isn't really a requirement. My problem is, since Ubuntu (and GRUB) wont see the SATA drive, I would have to switch the boot order in the BIOS to pick which OS to boot up.

So, I was wondering if:
1) There is someway to get Ubuntu to see my SATA drive
or
2) I can install Ubuntu on the IDE, and then somehow modify the Vista boot file to see Ubuntu so I can keep the SATA as my primary drive and not have to keep switching the boot orders.

Help!

Here is a question:

If he installs Ubuntu on the PATA can he just go ahead and edit grub with a proper menu item?


This is a typical GRUB entry for an M$ product.
```
title        Microsoft Windows Longhorn
root         (hd0,0)
savedefault
makeactive
chainloader  +1
```

Just add it into the menu.lst after Ubuntu is installed and set the timeout to 10.

---

### Post by celticbhoy on 2007-11-21
But first change the BIOS boot sequence to boot from the IDE drive.

---

### Post by meierfra on 2007-11-21
Boot from the live cd, open a terminal (application->accessories->terminal)
and post the output of 


```
sudo fdisk  -l
```
( l is a lower case L)

---


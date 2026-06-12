---
title: "installation woes"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ndoggendorf on 2007-04-12
ok so i'm working with a blank hard drive, when i try to run the installation i get this message

[17179571.552000] PCI: cannot allocate resource region 0 of device 0000:00:1b.0

then I see a black screen and cursor but can't do anything except ctrl-alt-delete which does what it does. 

specs:
MS-1022 notebook
geforce6200go TC
1 gb ram
2 ghz pentium M
80gb hitachi 7200rpm 8mb cache

any ideas would be much appreciated! Thanks!

---

### Post by CJay554 on 2007-04-12
blank hardrive? you would have to have some sort of OS to boot up a comp... wether it be windows or ubuntu... a blank hardrive is as good as a dead dog, unless your talking about a exterior drive?

---

### Post by Redache on 2007-04-12
My guess is you need to format the disk?

---

### Post by CJay554 on 2007-04-12
only way to format that im familiar with is running windows or ubuntu installations :/

---

### Post by ndoggendorf on 2007-04-12
its a brand new hard drive i bought. Last time i checked  they don't come shipped with OS's pre installed. its completely clean no OS, no nothing.

---

### Post by Boztech on 2007-04-12
What version of Ubuntu are you trying to install, and by which method (livecd or alternate install cd)?

Can you boot into a livecd environment on the machine?  Is your new hdd detected correctly in BIOS?

---

### Post by ndoggendorf on 2007-04-12
i've got both 6.06 and 6.10 on CD's and i can get to the startup screen (start/install, safe mode, etc...) but when i choose an option it loads the kernel, flashes that message I posted, goes to the Ubuntu loading screen for a few seconds and then the screen goes black except for a cursor and the only thing I can do from there is hit ctrl alt del and start over.

---

### Post by x8668x on 2007-04-12
ndogg,

Sounds like an xServer problem.  Search the forum for "Dealing with xServer" that should help you out.  BTW...does it do the same thing in recovery mode?  It shouldn't.  If it does, then it is not an xServer problem.

Good luck.:D

---

### Post by ndoggendorf on 2007-04-12
can't use rescue since this drive never had ubuntu on it to begin with, just tried installing a server version of 6.10, same mess...

i did however get a distro of Morphix to load for some reason even though it posted the same "cannot allocate" message. but without openoffice or working internet it's useless to me.

Also tried to install windows XP but the install locks up once it gets to the message "Windows is now starting."  

i'm at the end of my rope on this one....

---

### Post by ndoggendorf on 2007-04-12
Booyah found a fix

[http://trinityhome.org/phpbb2/viewtopic.php?t=259](http://trinityhome.org/phpbb2/viewtopic.php?t=259)

go to boot prompt 
type "live acpi=off noapic pci=bios " 

and watch her go!

thanks for everyones help

---


---
title: "I'm an idiot. help please"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Kyllc on 2007-01-11
guys, i am a complete linux noob.  I installed, by mistake, ubuntu server instead of the desktop version.  Now i cant reformat to install the desktop version.  HELP

---

### Post by null0 on 2007-01-11
yes you can. just do it.

---

### Post by taurus on 2007-01-11
Just run these commands from a terminal and you will get the desktop version on your machine.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by lyceum on 2007-01-11
What is preventing you? Can you boot from the disk?

---

### Post by xmastree on 2007-01-11
I think you can simply run
**sudo apt-get install ubuntu-desktop**
from your terminal to install the default desktop.

Edit: damn, too slow.

---

### Post by Kyllc on 2007-01-11
well, the computer isn't connected to the internet.  i have the CD though.

---

### Post by bulldog on 2007-01-11
If you have the server install cd,you've got a fair chance there's no ubuntu-desktop on it.
You have to download it or use the alternate cd.

---

### Post by xmastree on 2007-01-11
Or download the regular one, boot from it and start over. When the time comes to partition the disk, you'll have the option to reformat.

But, no internet on that box? It's gonna be plain...

---

### Post by jvc26 on 2007-01-11
Without the internet on your box the only way you can do it is to go to a place you can download from (work/friends/other pc) get the .iso for the Desktop version and reformat.

The other solution is hook yourself up to the internet and from the terminal line type:

```

sudo apt-get install ubuntu-desktop

```

Il

---

### Post by max_power on 2007-01-11
make sure your bios is set to check cd before hdd.

try pressing F2, F4, F8, or F12 when you first boot the computer to get into the bios

---

### Post by jvc26 on 2007-01-11
> **Kyllc said:**
> guys, i am a complete linux noob.  I installed, by mistake, ubuntu server instead of the desktop version.  Now i cant reformat to install the desktop version.  HELP

He'd already installed it to the HDD :) - The issue is now reinstalling without the Internet, for which he will either need to download the desktop version and reinstall or, connect the computer to the internet and sudo apt-get install ubuntu-desktop.

Il

---

### Post by lyceum on 2007-01-11
If you have no way to download and need it now, go to your local computer or book store. There are a few magazines sold this month (and every month for some) with an Ubuntu disk inside. Just an option. Make sure it is not a DVD disk if you have no DVD player though!

---

### Post by Kyllc on 2007-01-11
see, the thing is it wont let me re-install.  If i put the desktop cd in it just runs live cd.

---

### Post by Obor on 2007-01-11
Thats ok. Just run the live cd, wait for it to boot and then click on the Install shortcut on your desktop to install it onto the HD.

---

### Post by Kyllc on 2007-01-11
tried.  never loaded lol.  i'm about to wipe the HD with gparted i guess.  i can't fdisk, sudo fdisk cfdisk or anything!

---

### Post by lyceum on 2007-01-11
What are the stats of the PC; ram, hard drive, processor?

---

### Post by Kyllc on 2007-01-11
754 sempron, 256mb ram, 80gb sata drive

---

### Post by MkfIbK7a on 2007-01-11
i think the outcome of iyceums question is that you are going to have to use the alternate install disk....

---

### Post by Kyllc on 2007-01-11
any reasoning?

---

### Post by matt_risi on 2007-01-11
Either that or Xubuntu Alternate.

Reasoning: You don't have much RAM.

---

### Post by MkfIbK7a on 2007-01-11
yes you need an alternate cd because it just installs if you choose
 it doesnt go into the os so it uses much less ram
 i couldnt find a picture but it dsoesnt say 
start OR install
it says
Install in text mode
hope this helps

---

### Post by Kyllc on 2007-01-11
gotcha.  downloading the alt install.  We just ordered a 512 stick for the computer.  i think i've got the install working now though i just looked back at it.  we plan on using this box for a) experience with linux and b) a software firewall/manager for a wlan i'm setting up.

---

### Post by MkfIbK7a on 2007-01-11
hope you like it!:biggrin:

---

### Post by Kyllc on 2007-01-11
me too.  i've only used centOS.  and i just used kismet and some other wireless auditing software

---

### Post by Kyllc on 2007-01-11
found a 128 stick-o-ram and now it's working lol.  you guys rock my face.

---

### Post by MkfIbK7a on 2007-01-11
> **Kyllc said:**
> found a 128 stick-o-ram and now it's working lol.  **[SIZE="4"]you guys rock my face[/SIZE]**.

:confused: :confused: :confused:

---

### Post by xmastree on 2007-01-11
FWIW, my Athlon 600/256 desktop won't install ubuntu from the live disk, but works ok with xubuntu. It's the RAM.

---


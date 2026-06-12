---
title: "How to run both XP and Ubuntu on one laptop?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by vinc386 on 2008-03-05
Hi all,
i have a old laptop that currently running xp. i wanna know if it is possible to install ubuntu on the other partition of my laptop and i will be able to choose what OS i wanna run every time i boot my laptop(like startup menu that windows have).

**[COLOR="DarkOrange"]UPDATE: since the laptop doesnt have a wireless card, so i bought a Belkin 54G wireless adapter(PCI). the matter is it never works in ubuntu live-cd mode, so will it work after i install the entire os? or i should really find the driver somewhere else?[/COLOR]**

---

### Post by Snakob808 on 2008-03-05
Stick the ubuntu cd in and restart.  Install it on your empty partition.  The disc will automatically install the grub boot loader which will give you the option of which OS you want to use.

The installer for ubuntu is very easy to use and understand.

---

### Post by bodhi.zazen on 2008-03-05
> **vinc386 said:**
> Hi all,
i have a old laptop that currently running xp. i wanna know if it is possible to install ubuntu on the other partition of my laptop and i will be able to choose what OS i wanna run every time i boot my laptop(like startup menu that windows have).

Yes, should be no problem.

Install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by D3M0L1$H3® on 2008-03-05
Allthough, depending on how old it is, you may run into some annoyances due to it's old-ness.
and you only have 5 seconds to move between OS's on the bootloader, or it automatically chooses and boots Ubuntu.

---

### Post by bodhi.zazen on 2008-03-05
> **D3M0L1$H3® said:**
> you only have 5 seconds to move between OS's on the bootloader, or it automatically chooses and boots Ubuntu.

That can be configured by editing /boot/grub/menu.lst and increasing the time out.

[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

Scroll down a little.

---

### Post by vinc386 on 2008-03-05
thank you all!

---

### Post by vinc386 on 2008-03-05
> **D3M0L1$H3® said:**
> Allthough, depending on how old it is, you may run into some annoyances due to it's old-ness.
and you only have 5 seconds to move between OS's on the bootloader, or it automatically chooses and boots Ubuntu.

what kind of annoyances?
i bought my about 4 years ago. it's compaq m2000: 
Pentium M 1.7G, RAM 512+256Mb DDR1, 40G HDD, and on board video card

---

### Post by fettster on 2008-03-05
What about the other way around...
I am running Ubuntu and would like to install Windows XP as a second partition.  My laptop is already a dual boot of Ubuntu and Fedora, but I want to overwrite Fedora with XP.  Can someone tell me if this can be done safely, without wrecking my Ubuntu, and if so, how?

---

### Post by Drakkor on 2008-03-05
Go ahead and install windows,but it will over write the master boot record, so you just re install gruib,no problem,lol :)

---

### Post by fettster on 2008-03-05
> **Drakkor said:**
> Go ahead and install windows,but it will over write the master boot record, so you just re install gruib,no problem,lol :)

How do I do that?

---

### Post by oedha on 2008-03-05
just boot from windows installer cd...than install it on fedora partition....
after your windows installation finished......you can restore the grub by
foolow this link :==> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by vinc386 on 2008-03-06
> **Drakkor said:**
> Go ahead and install windows,but it will over write the master boot record, so you just re install gruib,no problem,lol :)

it sounds easy. it shoulda be like reinstall the entire windows, mayb u just need to fix the MBR files

---

### Post by Anubisxian on 2008-03-06
> **Snakob808 said:**
> Stick the ubuntu cd in and restart.  Install it on your empty partition.  The disc will automatically install the grub boot loader which will give you the option of which OS you want to use.

The installer for ubuntu is very easy to use and understand.

I had initially tried to use the GUI interface for partitioning and installation, but I found I had better luck using the text-based install, which should come up as an option when you boot from the Ubuntu dvd/cd. I almost always find that the text installer is quicker, regardless of the app.

---


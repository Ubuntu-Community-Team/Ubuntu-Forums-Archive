---
title: "Laptop"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by sleepwalker on 2007-10-15
I have finally took the plunge and installed Ubuntu Studio onto my HP dv2125nr laptop. I had no sound or wireless connectivity, but I applied updates and now my sound is working. I still do not have wireless access, and I see that this is a common problem.

Is there a way to kind of narrow down what I should look for? Is this  a 'restricted driver' problem?

Also, I was wondering if someone could link to to a way to edit the GRUB boot loader. I have about 10 entries now since I applied an update. Thanks.

Also, I notice that people have a registered computer number. How do I get one of those? They look cool.

Thanks. Tried to post all of my problems in a single thread to keep the forum neat.

Also, anyway to delete old topics I have posted?

---

### Post by ghost_ryder35 on 2007-10-15
got to find out your wireless card first, do an 
"lspci" to find it out

---

### Post by Keith_Burton on 2007-10-15
The grub menu is stored in /boot/grub/menu.lst. It's a regular text file and can be edited with "sudo gedit", "sudo kate", or your favorite text editor. I'm checking on your wireless and will post if I find anything useful.

You can get a registered number at Linux Counter: [http://counter.li.org/](http://counter.li.org/)

Keith

---

### Post by ghost_ryder35 on 2007-10-15
"**sudo gedit /boot/grub/menu.lst**" that will open up your grub menu in an editable doc.  you have to use the sudo command or be in a terminal session logged in as root to modify it

---

### Post by Keith_Burton on 2007-10-15
A Google search indicates your laptop has a Broadcom wireless chipset. Give this page a try: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Best of luck,
Keith

---

### Post by ghost_ryder35 on 2007-10-15
Make sure you have Universal Repositories checked
Wireless card using BCM43XX-FWCUTTER (requires wired internet connection, or a cd with the package on it)
**sudo apt-get update**
**sudo apt-get install bcm43xx-fwcutter**
**sudo modprobe bcm43xx**
then restart computer and all is good
iwconfig to check

---

### Post by michiel.patrick on 2007-10-15
The broadcomm card is not hard to get working and this is coming from a noob. Just follow that tutorial.

---

### Post by sleepwalker on 2007-10-15
Thanks everyone. That was a lot of help.

I am also encountering a problem. I am dual booting with Windows Vista. If I happen to mute the sound in Vista and shut the system down and boot into Ubuntu, I recieve no sound. Matter of fact, sound went away entirely. Any ideas? the laptop has quick access buttons, which Ubuntu can detect.

---

### Post by sleepwalker on 2007-10-15
Using lspci, I have:

01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Anywhere to check for updates on that?

---

### Post by sleepwalker on 2007-11-05
Upgraded to 7.10, and now everything is pretty doing what it is supposed to. Except for my sound. 

I am dual booting Vista and Ubuntu, and everytime I boot into Windows, I lose sound in Linux, until I randomly boot enough times for it to come back on. Then, if  happen to boot back into WIndows, the sound goes away again.

Any suggestions? Otherwise, I think I am gonna wipe Ubuntu.

---


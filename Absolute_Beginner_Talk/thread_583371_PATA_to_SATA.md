---
title: "PATA to SATA"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Riyonuk on 2007-10-20
I have two computers, a Dell and a Compaq. The Dell is new, and has a 250GB SATA drive. The Compaq has 2 PATA drives, 1 60GB and 1 80GB. All my music is on the PATA drives. How do I get those files to the SATA? I really dont want to use a USB over and over..

---

### Post by insane_alien on 2007-10-20
does the dell have a pata socket on its mother board? if not, use a patch cable to transfer them over(or a LAN, whatever you have) save you having to wear out your USB drive.

---

### Post by Riyonuk on 2007-10-20
Whats a patch cable?

---

### Post by loganm10 on 2007-10-20
chances are very very good that the Dell has a pata connecter, might only have one, and it might be plugged into a CD drive, but just unplug it, plug in the HDD and transfer it over to the SATA drive

Or you can buy a thing from your local computer store that is an adapter from IDE (PATA) to USB, and plug the IDE drive into a USB port

---

### Post by Dr Small on 2007-10-20
Here is what you need:
[http://www.satacables.com/html/sata-acessories.html](http://www.satacables.com/html/sata-acessories.html)

I bought one off ebay for a lower price, you can check there too.
It works great :D

---

### Post by jdong on 2007-10-20
Do you have a local network? You could transfer the files over the network by installing the "openssh-server" package on one system, then on the other connecting to it via "sftp://user_name@ip.address/" in Nautilus

---

### Post by Dr Small on 2007-10-20
> **jdong said:**
> Do you have a local network? You could transfer the files over the network by installing the "openssh-server" package on one system, then on the other connecting to it via "sftp://user_name@ip.address/" in Nautilus
Geesh... why didn't I think about sftp yesterday when I transfered 20 GBs of files to my system over the network... 
I had to use scp, which was still fast, though.

Dr Small

---

### Post by jdong on 2007-10-20
If you know how to use SCP, then the two are probably equivalent. SSH file sharing is extremely newbie-friendly because it's one package to install, no configuration, and Nautilus can directly connect to it (more advanced users can play around with SSHFS in universe to directly mount a SSH account as a directory!), secure out-of-the-box, and even serves in the future as a way to get a command-line remotely for administration. What more can you want out of one package? :)

---

### Post by Riyonuk on 2007-10-21
Can I connect with just an ethernet cable? Cause all I have is a DSL modem. I tried the ethernet thing, but both could not connect.

---

### Post by Dr Small on 2007-10-21
Looks like you need a crossover cable:
[http://kb.iu.edu/data/aeii.html](http://kb.iu.edu/data/aeii.html)

---

### Post by bobpur on 2007-10-21
From what I just read you're  in good shape if you're on a network. You could, also, get a CAT5 "Crossover" cable and connect both computers directly together at the network cards. The "crossover" cable is the direct way to do what your network does within the router.

                                                           Good luck

---


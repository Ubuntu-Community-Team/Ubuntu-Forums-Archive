---
title: "New 7.10 server user needs help!"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Waitrose Carpark on 2007-10-30
Hi there

I've looked through the documentation but I think I really need an idiot's guide - I'm a Windows user so Ubuntu is something I'd really like to get into.

Anyway, I have installed ubuntu 7.10 as a samba server as I intend to use it as a Windows server. It is a completely FRESH install, I haven't typed a single command yet (although I do have a little experience).

OK, now for my quickfire idiot's questions:

1. How do I access the linux command line from a network attached windows pc? So I can configure it?

2. I have the OS on an ATA disk and intend to have some SATA drives mirrored (built in RAID controller), I  will install the OS first, then add the drives, build the array and then try to share them out then, would this be an ok way to do it? Or maybe build the array first and do it all at the same time. All the partitioning confuses the hell out of me on the setup!

Or can anyone point me to a procedure I can follow? Any help is much appreciated!

---

### Post by DezSP on 2007-10-30
1. Run sudo apt-get install openssh-server on your Linux box and reboot it. Then download PuTTY onto your windows machine and use it to connect to your machine (just type in the computer name, port 22).

---

### Post by hyper_ch on 2007-10-30
reboot is not necessary after the installation of openssh-server

---

### Post by Waitrose Carpark on 2007-10-30
This is awesome and exactly what I need! What I didn't want to do was try stuff, install stuff and not know exactly what I was doing or if it needed/didn't need to be done. This is a great start! I am already in the server through putty, this is further than I managed to get in about 3 days of trying by myself!

Now I've seen several guides to setting up SAMBA servers but I already chose the SAMBA option when I installed Ubuntu. I just want a big, dumb, empty folder that ANYONE can access. I am assuming anonymous access is possible? (To the big dumb, empty folder at least?)

---


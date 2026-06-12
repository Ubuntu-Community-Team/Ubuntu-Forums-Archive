---
title: "Vgetty on Feisty setup problem"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by TechToys329 on 2007-08-11
I'm trying to set up Vgetty and ultimatey VOCP on Feisty. I have installed mgetty-voice 1.1.35-3ubuntu1 with Synaptic and received no errors. I an start vgetty from the command line with /usr/sbin/vgetty ttyS1 and see it with ps. When I tail the /var/log/mgetty/vg_ttyS1.log file I can see that it detected the USR 5610 modem, but it returns errors, probably due to starting vgetty from the command line. I tried creating an /etc/inittab file containing 

S1:345:respawn:/usr/sbin/vgetty ttyS1

but I cannot get vgetty to start that way. I also tried putting a ttyS1 file containing the same line in the /etc/event.d directory per a post that I read. Also without joy. I feeling that I'm stuck on the upstart thing.  How do I start vgetty properly?

---

### Post by patslap on 2007-09-23
Try this thread:

[http://ubuntuforums.org/showthread.php?t=148960&highlight=vocp](http://ubuntuforums.org/showthread.php?t=148960&highlight=vocp)

---


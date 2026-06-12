---
title: "login, ssh and remote desktop"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Hårek on 2006-08-12
Hi. I've managed to install ubuntu now, and finally got my wireless pci working (Ralink RT61)(!). I've managed to set up ssh, and can access it at least from inside LAN. Things are progressing, but I'm stuck on the following:

1. The ubuntu(dapper) machine will be stowed away without i/o devices and screen. It will be running a sshd. In case its accidentally turned off, it needs to log itself in automaticly when its powered up again. How do you fix this?

2. The sshd is set up and works. But when I log in through my windows(xp) machine using Tunnelier I end up in /home/media, which is good. But I can browse the entire filesystem, and that's bad. How do you "lock" the ssh-user to /home/media/.....? 

3. I would like to remote manage the ubuntu machine from other machines using ssh. Is it possible using only openssh, or do I need extra programs? (I've enabled remote desktop in system-> preferences)

ps. ssh is running on port 4891

tnx

---

### Post by steve.horsley on 2006-08-12
> **Hårek said:**
> Hi. I've managed to install ubuntu now, and finally got my wireless pci working (Ralink RT61)(!). I've managed to set up ssh, and can access it at least from inside LAN. Things are progressing, but I'm stuck on the following:

1. The ubuntu(dapper) machine will be stowed away without i/o devices and screen. It will be running a sshd. In case its accidentally turned off, it needs to log itself in automaticly when its powered up again. How do you fix this?

sshd runs as a daemon, as a service that starts up at boot time. So you will be able to connect to the machine after reboot.
> 
2. The sshd is set up and works. But when I log in through my windows(xp) machine using Tunnelier I end up in /home/media, which is good. But I can browse the entire filesystem, and that's bad. How do you "lock" the ssh-user to /home/media/.....? 

I don't think you can prevent the user looking round the reat of the machine when using ssh, but of course, they can't read or write files that the user they log in as can't access.
> 
3. I would like to remote manage the ubuntu machine from other machines using ssh. Is it possible using only openssh, or do I need extra programs? (I've enabled remote desktop in system-> preferences)
Openssh will give you a command-line login. This is probably all you need for managing a server. What's more, if you connect with "ssh -X" then you can run GUI applications on the server (e.g. nautilus) and the Xwindow will be tunneled back to the calling PC.

---


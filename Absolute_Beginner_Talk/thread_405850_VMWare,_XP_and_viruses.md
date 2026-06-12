---
title: "VMWare, XP and viruses"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Strider42 on 2007-04-10
Hi,

A quick n00b question for the Linux gurus.

I'm running VMWare Server with XP as the guest on Feisty Beta for a couple of essential Windows work apps.  Is it possible that if a virus hits the XP installation in VMWare that it could cause malicious damage to the host Linux system, or would it be contained within the guest OS?

Thanks in advance
Paul

---

### Post by machoo02 on 2007-04-10
I haven't used VMWare much (I use VirtualBox instead) but from what I understand about virtualization any virus that you would get in your guest OS installation would only affect that installation, since the guest OS thinks that it is the only OS running on the computer.  The other thing is that Windows virii cannot (AFAIK) cause damage on a Linux system.

---

### Post by aktiwers on 2007-04-10
Yes it will only affect the Virtual machine. 

Unless you have setup a network between your guest OS and the host, and the virus knows how to spread through networks, runs on  Linux or opens through Wine. Though opening through Wine only will affect your Wine folders and work when Wine is running. 

Though I also think you in this case would have to manually allow it to run through Wine.

So I guess my short answer is No. :)

---

### Post by Strider42 on 2007-04-10
:)   Ah, the joys of Linux.  Stress free computing :guitar: 

Thank you both!

---

### Post by Stink Hook on 2007-05-31
I was wondering the same thing. I guessed that it would be possible for a virus to access your Linux partition through a network connection of some sort but I wonder if it would be possible for a virus to corrupt data and spread a virus through a shared FAT partition that Linux and XP share. Maybe it would only corrupt the files and not acces Linus since it is highly unlikly the virus would be cross-platform. Hmmm...  :-k

---


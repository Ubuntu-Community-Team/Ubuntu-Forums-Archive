---
title: "How do I get to my network disk?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Crazychicken on 2007-07-15
on Windows I have a nice little program that mounts it, where do I go for Ubuntu?

(and, if I suspect a virus on that disk, how safe is it to copy stuff over from there to Ubuntu?)

---

### Post by jtraub on 2007-07-15
By default you can not run Windows programs in Ubuntu. So it is safe to operate with that disk.

Probably yu dhould try open Nautilus. File->Connect to the server

---

### Post by expatCM on 2007-07-15
Could you please describe what you are wishing to accomplish at the end of the day?   What does the Windows disk do for you when you run Windows?

---

### Post by Crazychicken on 2007-07-16
I have dual boot on my pc and there's a hard disk on our house network, sorry if I use imprcise terms but english is not my first language.

I have some files backed up on both my windows disk and the external one, only some are going  *poof* because of a virus, and I want to move everithing to Ubuntu.

I'm trying to understand how to open the network disk using Ubuntu.

---

### Post by Pheodax on 2007-07-16
Linux uses Samba to communicate with the Windows Network and it's shares.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

The tutorial is for setting up Samba to connect to Linux (might be useful if you can't connect to Windows, which is the problem I have here).

You first might want to try to install Samba if it's not installed yet:

sudo apt-get install samba

Then press ALT + F2 to bring up the "Run Application" menu. In there type: smb://xxx.xxx.xxx.xxx

In which xxx.xxx.xxx.xxx is of course the IP of the Windows host (the one with the shares).

---


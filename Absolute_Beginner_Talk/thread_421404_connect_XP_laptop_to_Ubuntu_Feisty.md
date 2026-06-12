---
title: "connect XP laptop to Ubuntu Feisty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by bennyb on 2007-04-24
I've been searching for 2 days for what I thought would be a simple answer. But it seems either no one else has this situation or I'm off course too far.

I solved the cryptic methods of sharing my ubuntu files with my XP laptops (samba installed, running, user and password configured) but am having a problem the other way around. My laptop icon shows on the ubuntu desktop after selecting Places-Connect to server... but in trying to browse gets me the message after about 30 seconds, "The folder contents could not be displayed." Could someone direct me as to what I'm missing. And maybe explain why this is so difficult (reminds me of Win98) to do without quoting "security issues."

---

### Post by mjitkop on 2007-04-24
In my house we have several PCs and laptops on a local network (both wired and wireless.) I was extremely surprised to see in Ubuntu that I could connect to the Shared drives of all the Windows XP machines on my network (that's all the PCs and laptops)! What really surprised me is that I did nothing at all after installing Feisty and I could access the network right away, it configured itself! :guitar: I haven't tried to connect to Ubuntu from XP though so I will have to try that. That's probably why you need to install Samba, I guess.

The easiest way I found to configure a Windows XP machine to share drives on your local network is to use the built-in Network Wizard in Start -> All Programs -> Accessories -> Communication. Choose the right configuration that matches your setup at home and check "yes" when asked if you want to share files and printers. That should do it.

---

### Post by dstew on 2007-04-24
Did you create a folder to be shared on your Ubuntu desktop?

---


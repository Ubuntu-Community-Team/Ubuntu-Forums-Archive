---
title: "How can I get my wireless adapter to work?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by karma2burn on 2006-04-04
O.K., well first off I have 2 computers at my house that were previously both networked together with a lynksys wireless-g broadband router and a linksys wireless-g usb network adapter.  I had windows XP Pro installed on both computers, until I realized that on the secondary computer, (the one with the usb network adapter) that windows XP needed me to activate it because you can only install one version of windows XP on one system at a time.  So, not wanting to pay $300.00 for another version of XP, I sought out an alternative.  Thus I stumbled upon ubuntu.  Anyway, the installation of ubuntu went just fine, but now I really have no idea how to get my usb network adapter to work with ubuntu.  The main computer I use is running XP still, (the one I'm using to type this), and I just want to know if it is indeed possible for me to network together these 2 computers I use similar to the way I had it before with XP.  I've tried to follow some of the steps I read in the forums, the ones dealing with using samba that is.  I went through the package installer and installed samba, but now I have no idea how to use it or anything.  I am a complete newbie with linux, so any help will be greatly appreciated.

---

### Post by nickj6282 on 2006-04-04
What is the model of your USB wireless adapter? USB adapters in Linux are problematic. Can you connnect with the wired network card instead? Also, get the output of 'lsusb' and paste it in here so we can see.

thanks
-Nick

---

### Post by karma2burn on 2006-04-04
Well, all I know about the network adapter is that it is a Linksys Wireless-G, 2.4 GHz 802.11g.  I'm not sure if that is the info you were looking for, but hopefully it helps.  Also, how do I go about getting the output of 'Isusb'?  Unfortunately I am also unable to connect with the wired network card as well.

---

### Post by nickj6282 on 2006-04-04
Umm, got a thumbdrive? You could copy and paste to a text file.

---

### Post by karma2burn on 2006-04-04
No... but how do I actually get the Isusb output anyway?

---

### Post by nickj6282 on 2006-04-04
Sorry, open up a terminal (Applications --> Accessories --> Terminal) and type "lsusb" (that first character is a L) and press enter. You might need root permissions ("sudo lsusb").

---


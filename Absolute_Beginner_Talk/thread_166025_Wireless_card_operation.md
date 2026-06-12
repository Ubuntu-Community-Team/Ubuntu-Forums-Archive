---
title: "Wireless card operation"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by oceanp on 2006-04-25
Hi,
I am using Breezy 5.10 installed from a CD from OSDisc.com and I have an SMCWPCI-G network card installed.  I am using Verizon DSL with their gateway.  I am trying to get this wireless card to work.
I understand this card has a driver which is “ath_pci/ath_hal” .  I cannot locate this file and am not sure what to do with it if I find it.
Can someone give me some detailed instructions?
TIA

---

### Post by user1397 on 2006-04-25
Have you tried "ndiswrapper" in synaptic? It's a program that can make some windows drivers work under ubuntu. Try searching "ndiswrapper" in these forums.

---

### Post by macdo on 2006-04-25
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

No guarantees, but try that link...
Wireless is notoriously hard to get working, so you'll probably need some patience. Don't give up, and don't hesitate to ask questions. If you can, copy the messages that you may get from the terminal.

Good luck!

---

### Post by Silver-revo on 2006-04-25
One tip I too had a tremendously hard time getting wireless to work...

Make sure that you have all of your network settings EXACTLY the way they need to be. I had one small setting changed and it would not function.
Also make sure you disable the other LAN driver if you have one.

Good Luck8)

---

### Post by Papa-san on 2006-04-26
My two cents is mostly in my signature links!

---

### Post by ubuntuuser on 2006-04-26
You can either use the link provided by macdo to get the latest linux drivers for your atheros chipset, or you can simply install the linux-restricted-modules paket for your kernel using synaptic or apt-get. If you just want to surf the web, I recommend installing the restricted-modules paket in the repositories. If you want to do some wireless security experiments, follow the MadWifi-HowTo.

---

### Post by hotpinkflamingo on 2008-04-18
I also have a PC with a smcwpci-g running Xubuntu, and the system recognizes the card and my wireless network, but when I try to make it connect it freezes up the system.  (Does the same thing with regular Ubuntu as well)
I'd like to try your restricted-modules suggestion.  How can I install them on a different PC than I used to download them?  Also, do I have to do anything once the package is installed?  Or will it simply "work"?
Thank you

---

### Post by hotpinkflamingo on 2008-05-13
Can anyone help please?

---


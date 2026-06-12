---
title: "Sharing Printer"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-06-06
A bit of background detail first :-

I have 2 pcs networked through a router (1 wired 1 wirelessly) the wireless connected pc is running on XP Pro and the wired pc is running on XP Pro & Feisty 7.04 (dual boot) and has a printer attached which is shared on the network in XP.

Clearly, when the wired pc is booted up intro XP Pro, I can connect and print from it via the wireless connected pc ...... question ?? can I do the same when the wired pc is booted into Feisty 7.04 ??

Please advise

THks in advance    SteveS

---

### Post by Seisen on 2007-06-06
What kind of printer is it. Some printers are a pain to get to work with Ubuntu.

---

### Post by dstew on 2007-06-06
Yes, you can share a printer in Linux just like you do in Windows. In the System -->Administration --> Printers dialog window, set sharing under the Global Settings tab. I assume the printer is already installed and working as a local printer in Feisty.

---

### Post by lazyart on 2007-06-06
It's gonna be a funny thing because you'll have to install that printer a second time on the wireless machine.  It will require a different entry for when the wired machine is running Linux.  And then when you print to it from the wireless you'll have to select the correct instance.  Physically it's the same computer and same printer, but as far as the network is concerned they are different devices.

If it's possible to make that printer into a network printer (either with a print server or maybe it has a network option) it will simplify things a whole bunch-- one printer period.

What kind of printer is it?

---

### Post by steve-shinn on 2007-06-06
Hi guys...it's HP Deskjet 710C which is installed and working fine on Feisty ...... I have got it shared now but it is clearly a pain in terms of the wireless attached pc having to effectively install it again !!:(

---

### Post by Wd2048 on 2007-06-06
Does this require Samba installed/configured? I have a Samsung laser printer that I am wanting to install on my Ubuntu machine and share it so that my wife can print from her WinXP laptop. Is it really as simple as sharing the printer? :o

---


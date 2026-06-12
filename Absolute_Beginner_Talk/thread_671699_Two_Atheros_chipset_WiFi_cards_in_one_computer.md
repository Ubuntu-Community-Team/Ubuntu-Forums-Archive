---
title: "Two Atheros chipset WiFi cards in one computer"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by pw2buz on 2008-01-18
Just installed 7.04 (Feisty Fawn) on an IBM Thinkpad T41, dual booting with Windows XP Professional.  Ethernet works fine, wireless doesn't.

I have NOT fooled with ndiswrapper, wicd, or other solutions yet.  I have two wireless cards because when I upgraded the Thinkpad's PCI 802.11b card to an Atheros chipset 802.11bg card, I broke one of the antenna
connections.  So I bought and installed a Netgear WG511R PCMCIA card,
which works fine with Windows XP.  Maybe sometime I will fix the broken
antenna.

I'm wondering if part of my trouble is that Network Manager sees two
wireless cards, ath0 and ath1.  And if so, can I disable ath0 (which I'm pretty sure is the built-in WiFi card)?  I'd like to have this happen automatically on boot, via a script.

pw2buz

---

### Post by Paulmd on 2008-01-19
> **pw2buz said:**
> Just installed 7.04 (Feisty Fawn) on an IBM Thinkpad T41, dual booting with Windows XP Professional.  Ethernet works fine, wireless doesn't.

I have NOT fooled with ndiswrapper, wicd, or other solutions yet.  I have two wireless cards because when I upgraded the Thinkpad's PCI 802.11b card to an Atheros chipset 802.11bg card, I broke one of the antenna
connections.  So I bought and installed a Netgear WG511R PCMCIA card,
which works fine with Windows XP.  Maybe sometime I will fix the broken
antenna.

I'm wondering if part of my trouble is that Network Manager sees two
wireless cards, ath0 and ath1.  And if so, can I disable ath0 (which I'm pretty sure is the built-in WiFi card)?  I'd like to have this happen automatically on boot, via a script.

pw2buz

Since you dug in to your computer far enough to break the antenna of your built-in wireless card, I presume you know how to access it. Just remove the miniPCI wireless card. Store it in an antistatic bag, as the problem is with the antenna, not the card.

ibm has maintenance videos on their website for many of their laptops, to show you how.

This will at least simplify the situation from figuring out if 2 wireless cards is a problem, or if it's just that you can't get the pcmcia card working. :)


As to why two wireless cards don't work... no reason offhand. Many computers have multiple ethernet connections. In fact I have put 2 wireless cards in one computer, it improved the reliability of a poor-quality wireless network (eventually the network got wired). It would favor one of the connections. This was an XP machine, so I can't say for sure it would work in Ubuntu.

---

### Post by pw2buz on 2008-01-22
Paulmd,

Thanks for your reply.  I don't want to dissasemble my T41 again if I can avoid it.  That's why I'd like to know if there is some way short of removing it to disable the PCI card.  Windows does it via Device Manager.  I wanted to try Linux because I'd like an alternative to Windows.

Pw2buz

---

### Post by kevdog on 2008-01-22
Do the following

gksu gedit /etc/rc.local

Within the file, bring down the interface you dont want and bring up the interface you want.  

Here is an example

ifconfig ath0 down
ifconfig ath1 down
ifconfig ath1 up

Save and exit the file.  Make it executatble

sudo chmod +x /etc/rc.local

No reboot, ath0 should be down on boot up.  You can reenable if you want at the command line with
sudo ifconfig ath0 up

---


---
title: "No Gigabit LAN, only 100Mbit"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by barthi on 2007-06-26
Hi!

I installed Ubuntu 7.04 on an AMD 64 X2 3600+. My mainboard is the ASUS M2A-VM HDMI.

Everything seems to work fine.
But my network adapter only operates with 100mbit instead of 1000mbit.

lspci shows the following infos about the lan adapter:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

Can anyone please tell me, where's the problem?

Thanks,
barthi

---

### Post by jkeyes0 on 2007-06-26
what sort of router or switch do you have the computer connected to?

---

### Post by Rocket2DMn on 2007-06-26
Your router/switch has to support and have gigabit speed enabled, and you also need a CAT5E or CAT6 ethernet cable.  Then, you need to be sure you have gigabit drivers installed for your card.

---

### Post by barthi on 2007-06-26
Well, ok. The switch supports Gigabit-LAN. I already tested it under WinXP.

But what do you mean by the correct drivers? Where do I find them, how do I install them?

---

### Post by Rocket2DMn on 2007-06-26
Actually it looks like you have a good driver installed - you may have to configure the card to run at gigabit speed though.  I don't run my card at gigabit speed, so you may have to dig around for that a little bit since I don't have experience with it.  It may require that you install a different network manager or configure a file somewhere, hopefully somebody else has more detail on that.  Good luck.

---

### Post by el_rico on 2008-01-20
I also have this problem (with the same MB). I do not have the possibility to test under WinXP, but the status LED clearly indicates that the speed on the cable is 1Gbps. Have you found a solution?

EDIT: As far as I'm concerned, I have found a solution. It seems that something is wrong in the Samba client. I have tried to mount my Smb share using ```
sudo mount -t cifs //corniflower/Data smb -o ip=192.168.0.10,iocharset=utf8
``` and now it is transferring at around 25MBps (was 7MBps before).

---


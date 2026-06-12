---
title: "Internet connection"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by mikeman on 2008-01-12
Hi guys. I just installed Ubuntu on my machine alongside WinXP. I now want to connecto to the internet. I have a Telindus 1131 ADSL Router(USB). What exactly must I do so I can browse the internet with Firefox? Thanks.

---

### Post by erginemr on 2008-01-12
Hi there!

Do you happen to have an ethernet slot in your modem? And an ethernet card in your computer?

EDIT: Also check out the following thread please, if you haven't done already:
[http://ubuntuforums.org/showthread.php?t=237641](http://ubuntuforums.org/showthread.php?t=237641)

---

### Post by mikeman on 2008-01-12
No, I don't have an ethernet card...

---

### Post by bagguley on 2008-01-12
The ethernet solution is definitly the one to take if you can. However if not have a look at [https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem) . Ive never used one with Linux before and i do know theyre a pain in the ****. The easiest solution would be to buy an ethernet ADSL modem/router from amazon or where-ever for about £30.

---

### Post by erginemr on 2008-01-12
The following site lists a Telindus modem (but not your series I believe) as having an eagle chipset:
[http://ar.geocities.com/novatocba/doc/frame/modem-blog.htm](http://ar.geocities.com/novatocba/doc/frame/modem-blog.htm)

I am also using a cheapware USB win-modem, Sagem F@st 800, had difficulties at first in installing it to Ubuntu, but finally managed to install it manually. Lately have I found a program that does the same with much less effort:
[http://wiki.ubuntu-fr.org/materiel/modem_sagem_fast_800](http://wiki.ubuntu-fr.org/materiel/modem_sagem_fast_800)

The program consists of three parts:
[http://perso.orange.fr/j.m.e/ueagle-data_1.1-0ubuntu0_all.deb](http://perso.orange.fr/j.m.e/ueagle-data_1.1-0ubuntu0_all.deb)
[http://perso.orange.fr/j.m.e/installemodem_0.0.3-0ubuntu1_i386.deb](http://perso.orange.fr/j.m.e/installemodem_0.0.3-0ubuntu1_i386.deb)
[http://fr.archive.ubuntu.com/ubuntu/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb)

First one is the modem firmware, the second is the graphical installer, and the third is a library required by the installer (I believe it had already been installed by default in Ubuntu). The program is in French but instructions are quite straightforward and easy to follow. You may consider trying your chance with it.

---

### Post by naugiedoggie on 2008-01-12
> **mikeman said:**
> Hi guys. I just installed Ubuntu on my machine alongside WinXP. I now want to connecto to the internet. I have a Telindus 1131 ADSL Router(USB). What exactly must I do so I can browse the internet with Firefox? Thanks.

According to the datasheet available[ **here**]("http://www.oneaccess-net.com/telindus/products/broadbandcpe/1130-1131adslrouter.php"), this modem has both a USB and an Ethernet connection.  I'd recommend spending the $25 for an ethernet card (assuming you don't have one available), as it will give you a faster and more stable connection than the USB line.

If you have any friends who are into computers, you could just ask around -- I personally must have 6 or 8 of these things lying around, accumulated over the years from various computers tossed out and old DSL modems.  The phone company ships them for free with new modems now (although sometimes you have to ask).

Thanks.

mp

---


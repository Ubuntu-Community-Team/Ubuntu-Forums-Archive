---
title: "Would these hardware work with ubuntu?"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by orhon on 2005-10-12
Hi,
i have an ubuntu install CD and Dell Latitude 110L. Would i work these hardware under ubuntu? thx :)

Intel®  Pentium®  M Processor 735
Integrated 56 Kbps2 V.92 modem and 10/100 Ethernet LAN(Ethernet card is manufactured by Intel)
Bullet	Intel®  PRO/Wireless 2200 802.11b/g WLAN miniPCI card
Intel®  910GML integrated UMA graphics chipset
SigmaTel C-Major Audio

---

### Post by matthew on 2005-10-12
I don't know about the modem or the sound card, but everything else should work well. Those may work fine as well, I just don't have any experience with that exact hardware.

---

### Post by orhon on 2005-10-12
thnx =)

the problem is that i am a university student and i use wireless at school, wired connection at home. these are must for me. :)

i hope i will be able to install ubuntu soon :)

---

### Post by samoht625 on 2005-10-12
try the live cd first:-).. if it's good, then i would think that all the hardware is supported.

---

### Post by orhon on 2005-10-12
i tried the live cd
sound card and screen worked pretty well, but it worked slowly so i couldn't test network cards.

also i saw a post on these forums:
[QUOTE=levelx]Hi all! I'm new to Ubuntu and this is my 1st post.
I have just tried Ubuntu on my Dell Latitude 110L laptop and guess what? After the install all i could see was a black screen. I searched the web/forums/wiki etc and i found nothing.

I tried to configure X with xorgcfg and xorgconfig but i still couldn't open display.
I fixed this issue doing this:
Switch back to runlevel 3, kill all X and gdm.
Edit /etc/X11/xorg.conf.
Go to the section of the video card.
Replace "i810" with vesa. Save and "startx".
It magically works. I have seen on many forums people looking to fix this.
Dell Latitude 110L uses graphics card Intel 910GML chipset with UMA graphics (up to 64MB shared). No drivers found.
I'm looking forward to configure my Wireless Net card too (Broadcom is also unsupported).
Cya![/QUOTE]

---

### Post by orhon on 2005-10-12
umm i have another problem now.

I am trying to use Ubuntu in Turkish. At first, it says it needs to update some files since my language is not completely integrated. Since i don't have a net connection, i skipped that and it opened a half-Turkish system. I am making Turkish Q keyboard the default one but it still doesn't recognize my keys. Does this problem can be solved when Ubuntu is updated?(an error appears after closing keyboard preferences but my preferences are saved)

thx

btw error says: activating xkb configuration

umm i found the answer but it says give the command dpkg-reconfigure locales

where do i use these command ?
sorry i am completely a newbie :)

---


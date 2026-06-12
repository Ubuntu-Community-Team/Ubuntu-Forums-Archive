---
title: "Grud doesnt show up after install"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by geller on 2008-01-22
I have an Acer Aspire 5315 laptop. There was XP installed. Then I shrinked the main drive and a installed Feisty. All went fine until  reboot. The computer didin `t recognize the sata ahci drive as a booot disk and cant get to grub prompt. Still I can boot up XP with the live cd and Feisty too. The cd came from Shippit and I cant just download the newer version because of dialout connection. For the information with a little fiddeling around the sound is usable /new alsadriver package snd-hda-intel/ Ethernet card is ok .I don’t have wifi connection so didn’t tried ,but its been said that works with XP drivers and ndiswrapper. The graphic c  card is intelx3100 works in vesa mode and has drivers in gutsy. The internal modem doesn’t work Agere Hda /11c1040/ with or without patching. The connection just times out. What makes me a lil bit nervous that I cant  boot  without cd. I tried it with sam linux 2007 /basically pclos 2007/ and Dreamlinux /Debian etch/ and all the same.

---

### Post by aashay on 2008-01-22
I would say reinstalling grub via the live cd would be the most sensible option:

> 1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

I dint write these, wernst did here: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
Just pasted them here for your referral

---

### Post by geller on 2008-01-23
It not gonna work. I mentioned earlier, that i can boot the newly installed system via livecd. Tried to install grub to MBR ant d after to root partition. None works this time. I have been using linux since 1997 but never had that kind of problem. True, that it is my first laptop and SATA AHCI harddisk. I hope that it is fixed in newer releases. But was quite disappointed I had various driver problems but never with harddisks. Now I reinstalled windows XP and waiting for viruses. Gonna make another try when I get broadband and it will be possible to download newer release with my favourite development tools. Its a strange error however.

---


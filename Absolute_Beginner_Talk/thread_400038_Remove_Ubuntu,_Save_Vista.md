---
title: "Remove Ubuntu, Save Vista"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by patchmonkey on 2007-04-03
Hi,

A few weeks ago, I tried to install 6.06LTS (64-bit) in a dual-boot situation with Windows Vista and, to make a long story short, I had to format and wipe my entire computer - there was just so  much wrong, and it was so difficult to recover, that it was easier to do that.

So, today, I figured that perhaps the problems I had before had been fixed in the latest beta of Ubuntu (7.04) - however, it doesn't seem like they are. I'm running a Dell D620, and it doesn't recognize my wireless card (DW1490) (and in fact, it had disappeared entirely on the last reboot), it doesn't seem to want to acknowledge that I have a NVidia Quadro110 (defaulting to no-acceleration), etc.

However, I'm a bit nervous - I figured I could use EasyBCD to revert the MBR to the Windows Vista bootloader, but no nice, it remains with Grub. How can I repair this situation? Obviously, both OSes work - Vista correctly and Ubuntu is bootable (although not entirely usable). I would be happy to continue using Ubuntu if I could repair the wireless issue, although it doesn't seem likely from what I see in the forums; in the alternative, how can I remove Ubuntu and reclaim the hard drive space without destroying my Vista installation at the same time? My fear, of course, is that if I repartition the Ubuntu partition, since I cannot seem to change the bootloader using EasyBCD, I won't be able to boot into Vista anymore at all. (This seems like a possible solution - [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) - but I'm still wary.)

Thank you for any advice!

---

### Post by heimo on 2007-04-03
> **patchmonkey said:**
> 
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)


Yeah, try that one, looks appropriate.

---

### Post by nudnik on 2007-04-03
> **patchmonkey said:**
> Hi,

A few weeks ago, I tried to install 6.06LTS (64-bit) in a dual-boot situation with Windows Vista and, to make a long story short, I had to format and wipe my entire computer - there was just so  much wrong, and it was so difficult to recover, that it was easier to do that.

So, today, I figured that perhaps the problems I had before had been fixed in the latest beta of Ubuntu (7.04) - however, it doesn't seem like they are. I'm running a Dell D620, and it doesn't recognize my wireless card (DW1490) (and in fact, it had disappeared entirely on the last reboot), it doesn't seem to want to acknowledge that I have a NVidia Quadro110 (defaulting to no-acceleration), etc.

However, I'm a bit nervous - I figured I could use EasyBCD to revert the MBR to the Windows Vista bootloader, but no nice, it remains with Grub. How can I repair this situation? Obviously, both OSes work - Vista correctly and Ubuntu is bootable (although not entirely usable). I would be happy to continue using Ubuntu if I could repair the wireless issue, although it doesn't seem likely from what I see in the forums; in the alternative, how can I remove Ubuntu and reclaim the hard drive space without destroying my Vista installation at the same time? My fear, of course, is that if I repartition the Ubuntu partition, since I cannot seem to change the bootloader using EasyBCD, I won't be able to boot into Vista anymore at all. (This seems like a possible solution - [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) - but I'm still wary.)

Thank you for any advice!

Bring up the command prompt using a Vista installation DVD in "repair" mode. Instruct the DOS prompt to access the C drive (or whatever disk Vista is installed on)  and type the following: bootrec/fixmbr     That will restore the Vista bootloader.

---

### Post by Spr0k3t on 2007-04-03
I'm curious... have you tried installing the nVidia drivers?  Also, the DW1490 (Broadcom based chipset) is going to be a bear to get working.  Your best bet for network would either be through a wired connection (cat5e) or by purchasing a card with better driver support for linux.

---

### Post by Doug11 on 2007-04-03
I don't know why people want to change and leave Ubuntu. I have always been an XP user until I saw someone talking about Ubuntu on TV once and I thought 'what the heck, I'll give a try" It took a lot of trials and error, reading the forums and playing with the machine to get used to it. I had one partition which was Ubuntu and it took about two weeks to finally get it set up the way I wanted it. I used Ubuntu and only Ubuntu for about two months and then Vista was released, so I thought I's see what all the hype was about, so I found me a copy, made a little partition and let it go. Well, after about an hour into it and about four ctrl+alt+del's, and about the same amount of freeze-ups, I was not impressed. So now I'm back to Ubuntu happy as a clam.

---


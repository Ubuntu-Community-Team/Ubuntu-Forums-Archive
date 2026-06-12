---
title: "Installing Ubuntu without Grub"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-05-22
Well, since booting ubuntu is giving me endless troubles because of errors in Grub stage 1.5 (16, 21 and 23) i wanna know if it is possible to install ubuntu without Grub. You know, like Win**** uses to install. 
I tried to change the HDD type to "Normal", "match partition table" and "Large", but it was no use (btw i have a 40 GB IDE HD). I googled a lot, even posted on this forums and i came up with replies like "it might be a grub bug, get the latest one" and "run fsck to check for errors in your HD". I have already the latest grub version and i also run fsck but no use.

---

### Post by Kobalt on 2007-05-22
I actually don't believe you can install Ubuntu without a Grub, or even a boot loader. Grub2 is coming soon, maybe in Gutsy, have you searched for it yet as a possible solution ?

---

### Post by ThinkBuntu on 2007-05-22
> **Kobalt said:**
> I actually don't believe you can install Ubuntu without a Grub, or even a boot loader. Grub2 is coming soon, maybe in Gutsy, have you searched for it yet as a possible solution ?
That's wrong. Look into booting with LILO. You'll need to do it manually, and it'll take a little work, but again, a bootloader's a bootloader. There's no special "GRUB compatibility" with Ubuntu.

EDIT: I don't have my Ubuntu laptop with me, but this evening I'll try to switch my bootloader to LILO if I have the time. Check back on this post tomorrow if nobody gives you a how-to for LILO with Ubuntu.

---

### Post by Cypher on 2007-05-22
> **Kobalt said:**
> I actually don't believe you can install Ubuntu without a Grub, or even a boot loader. Grub2 is coming soon, maybe in Gutsy, have you searched for it yet as a possible solution ?
More correctly, you have to use either GRUB or LILO to boot Linux. You are welcome to use the Windows boot loader as a way of selecting Linux or Windows but to actually get Linux to load, you will still need one of those two.

If GRUB is giving you lots of trouble, LILO may be the other option. I don't believe it is available by default, so you will need to get the LILO package installed first.

---

### Post by ferpadro on 2007-05-22
wow...thanks for the quick replies. Actually im a bit worried, coz after trying all this solutions i came up to think this is a HDD problem or (i hope not) a Motherboard problem. Its so strange, the grub errors only pop up when i leave my machine turned off for a long period of time, lets say, 8 hours. But if i manage to enter Ubuntu for first time in the morning, and then i need to restart the machine everything goes neat. Could it be a heating problem?

Anyways, thanks to all of you, i think ill give LILO a try :D

---

### Post by ferpadro on 2007-05-22
ok, i downloaded LILO and before i did anything this message popped up:

 WARNING!                                                                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Your /etc/fstab configuration file gives device                           &#9474;  
 &#9474; UUID=4eccbc2f-7619-4474-9e52-6014419f203d as the root filesystem device.  &#9474;  
 &#9474; This doesn't look to me like an "ordinary" block device. Either your      &#9474;  
 &#9474; fstab is broken and you should fix it, or you are using hardware (such    &#9474;  
 &#9474; as a RAID array) which this simple configuration program does not         &#9474;  
 &#9474; handle.                                                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; You should either repair the situation or hand-roll your own              &#9474;  
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474;  
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474;  
 &#9474; found in /usr/share/doc/lilo/.   

BTW, im not using any type of RAID configuration (i can barely afford 1 HD xD), so i guess my fstab is broken. Any ideas on how to repair it?

---

### Post by ferpadro on 2007-05-22
bump

---

### Post by ugm6hr on 2007-05-23
Might be worth checking the HD with a diagnostic utility:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
has most manufacturers on it - or just get one from the manufacturers website (I know Hitachi have them).

Unfortunately, you will have to reboot to do this - hopefully you'll be able to get back in afterwards!

---

### Post by Soarer on 2007-05-23
I couldn't use grub either - it just hung at stage 1.5. This was my first Ubuntu install, so I was worried :(

I found some documentation on LILO (there's loads on the web) and used that instead. It has worked fine for more than a year, upgrading from Dapper to Fiesty without missing a beat.

You might want to try upgrading your BIOS first, it may be that grub will work then, but at least you will have the latest version if you decide to use LILO.

---

### Post by ferpadro on 2007-05-23
I found out that lots of people had this same error while installing LILO. They said to modify the /etc/fstab file, i did it correctly but liloconfig keeps throwing the same mistake. I really dont know what to do...  Seems that ill need to download Ultimate Boot CD. I`ll do it and post the results here

thanks in advance

---

### Post by ferpadro on 2007-05-23
i did a e2fsck while running a live CD and it didnt detect any corrupted or damaged block. I downloaded Ultimate Boot CD as an ISO image, burned into a CD, changed my BIOS to boot from CD player, but it doesnt load, i dont know what went wrong.

I have two option left, or configuring LILO (but then i am stuck exactly in the same problem, when i do a liloconfig it says: "UUID=4eccbc2f-7619-4474-9e52-6014419f203d as the root filesystem device. This doesn't look to me like an "ordinary" block device.") or update my BIOS, but im very scared to do this coz i wont just damage the HD if something goes wrong, but also my whole computer, since BIOS is the core of booting.

If someone who is reading this did sometime a BIOS update without being harmed, id be very thankful if you can post any possible solution or a step-by-step BIOS update guide.

Thanks in advance

---


---
title: "Installing on Gigabyte DS3 Jmicron RAID array."
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by &gt;HyperlogiK&lt; on 2007-04-18
Excuse this very noobish first post, but google didn't turn up anything. I have a Gigabyte DS3 with 2x Seagate 7200.10s in RAID 0 running on the Jmicron SATA controller and a single 120 GB IDE disk. Windows XP and the MBR are on the RAID array. What is the easiest way for me to install Ubuntu? Can I put it on the IDE drive and then fix RAID drivers and the bootloader once it is installed? What would I need to do to install on the RAID array?

Thanks, your help is appreciated.

---

### Post by overdrank on 2007-04-18
> **>HyperlogiK< said:**
> Excuse this very noobish first post, but google didn't turn up anything. I have a Gigabyte DS3 with 2x Seagate 7200.10s in RAID 0 running on the Jmicron SATA controller and a single 120 GB IDE disk. Windows XP and the MBR are on the RAID array. What is the easiest way for me to install Ubuntu? Can I put it on the IDE drive and then fix RAID drivers and the bootloader once it is installed? What would I need to do to install on the RAID array?

Thanks, your help is appreciated.

Hi and welcome. Installing ubuntu on a ide drive with the raid will cause problems it did for me and others. You can install it on the raid with no problems because as I understand it ubuntu see it as fake raid. Here is a couple of links to help you understand
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Hope this helps and good luck! :D

---

### Post by kpel on 2007-04-18
> Hi and welcome. Installing ubuntu on a ide drive with the raid will cause problems it did for me and others.

It did for me, though I don't know if this was due to my newb-ness or problems with the specific configuration.  I have the GA-965p-ds3 with 2 drives in RAID0 and two hooked up as IDE, though everything is now set to IDE (though still hooked up to the same ports).

I had intended to do the same thing you want to, but it didn't work out.  I installed to the IDE drive but kept getting an Error 20 out of GRUB, soft reboot would then show my RAID array as failed though a hard reboot would solve that problem.  I managed to then accidentally partition one of the RAID drives, so that ended my Windows install right there.  Luckily I had backed up since I figured I'd do something like that. :-s 

Right now I'm running XP on one drive, Ubuntu on the other and the remaining two are currently formatted for NTFS, though I'm probably going to change one to use with Ubuntu.

If you do find a way to make it work, let me know.  I wouldn't mind getting my RAID0 back.

---

### Post by &gt;HyperlogiK&lt; on 2007-04-19
OK, thanks a lot guys, will give it a shot today.

---

### Post by axylone on 2007-04-19
I have the same motherboard, but with two SATA Raptors in RAID 0 with xp and vista already on them.  I'm installing 7.04 today (first time using ubuntu, or linux for that matter), hopefully I can get triple boot working.  We'll see what happens

---

### Post by redbull_monsta on 2007-04-20
I have the same board and 2 western digitals on the Jmicron RAID - I found i could get SUSE and Fedora Core 6 to detect the RAID but had issues after intall - not able to boot

The Fiesty BETA would not detect the RAID controller atall

The only way i got RAID enabled was with the Gentoo 2006.1 live CD

Hope Fiesty does work - i will install it too - keep us posted!!!

---

### Post by redbull_monsta on 2007-04-24
Well.......

I cant get the live CD to boot fully.

I have tried every option i can think of, full specs below

CoreDuo E6400 @ 3.2ghz (tried at default too)
768mb XFX Nvidia 8800 GTX
4096mb OCZ Gold DDR2 @ 800mhz
2x250gb SATAII - Raid 0 
Audigy 2 PCI sound card

I have I have tried with onboard LAN enabled/disabled
I have tried with onboard sound enabled/disabled

I have tried with NO RAID or SATA drives
I have tried with 1 Pata HD
I have tried with both SATA HD's split from RAID and on 'normal' SATA ports

no luck just get lockup during load, yellow bar 3 1/4 'notches' along on gui

help !

---

### Post by kpel on 2007-04-24
Sounds to me like you've got a bad CD.  Run the LiveCD check first and see what you get.  I know that was my problem with several CDs (crappy media) so I ended up burning the CD at 12x and then everything worked.

This is the setup that I'm curring running a dual-boot setup fine with:

Onboard audio ON
Onboard LAN ON
Drives work as IDE
USB Keyboard/Mouse
All of the other BIOS options are at the defaults (F10 BIOS)
Two drives on the RAID ports, two on regular ports.

Ubuntu has no problem recognizing any of the drives, or installing to any of them.

Side note:

For anyone trying to install Ubuntu on a seperate drive and maintain a XP install on a RAID0 array, be careful.  From what I've gathered the install process worked fine, but the GRUB bootloader installed on **one** of the drives in the RAID0 array--thereby nuking my array and any chance of fixing the MBR.  I don't know if installing GRUB on the Ubuntu drive and changing the boot order would have worked and I'm not about to reinstall XP again (it's such a PITA compared to Ubuntu).

---

### Post by redbull_monsta on 2007-04-24
> Sounds to me like you've got a bad CD. Run the LiveCD check first and see what you get. I know that was my problem with several CDs (crappy media) so I ended up burning the CD at 12x and then everything worked.


OK i will re-burn the ISO and try again, i am on the F10 BIOS too, What revision board is yours? v1.00 here

---

### Post by kpel on 2007-04-24
> **redbull_monsta said:**
> OK i will re-burn the ISO and try again, i am on the F10 BIOS too, What revision board is yours? v1.00 here

v1.00 as well.  I was due for a complete system upgrade when Conroe launched so I hopped on the earliest (good) available hardware.  Heck, I had to buy an OEM CPU because I couldn't find it retail.  The floppy port on my board was DOA, but I never bothered to RMA it since I wasn't planning on using a 3.5".  Gotta love USB booting. :)

---

### Post by redbull_monsta on 2007-04-25
OK 

The 32 bit version works
The 64 bit version doesnt (tried 2 CD's both burnt @ 8x and checked)

---

### Post by redbull_monsta on 2007-04-26
Well iv'e gone back to Vista 64bit for the time being.... :(

---


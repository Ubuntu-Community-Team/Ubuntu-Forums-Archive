---
title: "refusing to boot from cd - PLEASE HELP!"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by kimlatraductrice on 2006-05-30
Hi, 
I really need someone's help to figure this one out. My laptop refuses to boot from a Linux CD - whether it's a Live CD or an Install CD. The error message I keep getting is:

Checking Boot CD-ROM...
Boot CD-ROM type: Non-Emulation Booting *(What does this mean?)*
ISOLINUX 2.04 2003-04-16 isolinux: Image checksum error, sorry...
Boot failed: press a key to retry...

I downloaded and burnt the iso image onto three different CDs, twice with Breezy and once with Dapper - all the CDs work in my PC so it doesn't make sense that it's really a checksum error. I finally just tried to use the Install CD I ordered online, just to see if it would boot, and I got the **exact same **error message.

I googled the error message and came up with forums in a different language... so I know someone has had this error too in the past, but I can't read what they're saying about it!

I'm wondering if somehow my laptop (HP Pavilion zt1210), which came with XP pre-installed, is somehow preventing another OS to be booted from CD? My DVD-ROM driver has a driver "signed by Microsoft"... could that be the problem?... or maybe the drive itself is broken somehow?

Could I copy the iso image onto an external hard drive, like an iPod, for example, and boot from that?

Is there any way to get around this problem?

Many, many thanks for any help you can provide... I really want to install Ubuntu on this laptop!

---

### Post by aysiu on 2006-05-30
Instead of just guessing the probability it's a checksum error, do an actual checksum yourself--even the ShipIt CDs can be corrupt.

Look at the first half of this tutorial:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by catlett on 2006-05-30
Go into your bios. Some bios have a section where you enable "non-emulation booting enabled " to boot from the CD.
Do you know how to enter your bios? It's accessed from the quick splash screen Iof your computer makers logo at startup  before windows starts up . It will say enter F1 or F12 , F something to enter menu or enter setup. This will take you to a text menu which is the bios menu. Look for the boot option and check for non-emulation booting.

---

### Post by kimlatraductrice on 2006-05-30
[QUOTE=aysiu]Instead of just guessing the probability it's a checksum error, do an actual checksum yourself--even the ShipIt CDs can be corrupt.

Look at the first half of this tutorial:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)[/QUOTE]

Thanks, aysiu, I followed your tutorial to a tee (it was great!) - I ran checksum verifications on all of the CDs (even the one I ordered from thelinuxstore.ca), and they all passed. I'm guessing the problem is more with my laptop than the CDs since I can boot from the CDs in my PC.

---

### Post by kimlatraductrice on 2006-05-30
[QUOTE=catlett]Go into your bios. Some bios have a section where you enable "non-emulation booting enabled " to boot from the CD.
Do you know how to enter your bios? It's accessed from the quick splash screen Iof your computer makers logo at startup  before windows starts up . It will say enter F1 or F12 , F something to enter menu or enter setup. This will take you to a text menu which is the bios menu. Look for the boot option and check for non-emulation booting.[/QUOTE]

I went into BIOS, and the only options it offers me in the boot menu are a list of the bootable devices - hard drive, CD-ROM, floppy; I can select one of those but that's it, I have no other options.

And non-emulation booting seems to BE enabled already...

---

### Post by solarwind on 2006-05-30
Yeah, my laptop wont even boot from the live CD. It will boot from the install cd though. Laptops are sometimes a little different than desktops. Make sure you check the bios settings for anything funny.

---

### Post by catlett on 2006-05-30
I was hoping it would be that simple. When you choose cd does the same error come up? If so you might have to look at alternative ways to install.
So check off cd and see if it still doesn't work. Next question is do you have internet access with this laptop?

---

### Post by Sef on 2006-05-30
If you can't get the CDs to boot, look at a [Netboot Installation]("https://wiki.ubuntu.com/Installation/Netboot?action=show&redirect=NetbootInstall").

---

### Post by kimlatraductrice on 2006-05-31
[QUOTE=catlett]I was hoping it would be that simple. When you choose cd does the same error come up? If so you might have to look at alternative ways to install.
So check off cd and see if it still doesn't work. Next question is do you have internet access with this laptop?[/QUOTE]

Same error when I choose CD. Stupid laptop, argh!

I don't have Internet access right now since I don't have a wireless card, but I could always hook it up to our network at home (wired). 

The problem with a Netboot install, though, is that I can't test out the Live CD first to see if all my hardware is supported. I wouldn't want to just go ahead and install it and then find out that nothing works with it... this is my first time installing Ubuntu (or any other distro), so I'd like to be able to play with it for a week or two before plunging into the install. I've looked around a bit on the Live CD on my PC, but I still need to know if it's compatible with my laptop.

---

### Post by hotbrainz on 2006-05-31
I have a HP laptop too.. I took the plunge a couple of months back and now have almost all the things working. No worries... just go for it. These forum geniuses are too good and too kind. They always help. So install after u backed up all your data.

---

### Post by kimlatraductrice on 2006-05-31
[QUOTE=hotbrainz]I have a HP laptop too.. I took the plunge a couple of months back and now have almost all the things working. No worries... just go for it. These forum geniuses are too good and too kind. They always help. So install after u backed up all your data.[/QUOTE]

Thanks for the encouragement :) I really really do want to just take the plunge... I just hope I won't regret it later!

But I guess I'll try the Netboot thing tonight. Does anyone have any **clearer instructions** than what's in the wiki? There's a lot of stuff I don't understand in there, it'd help if someone could "dumb down" the installation for me...

---

### Post by catlett on 2006-05-31
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm) That may solve the problem. First you need to get the smart boot manager on a floppy. Then you boot to the floppy. (make sure to switch bios to floppy) When the boot manager starts from the floppy it will have a mernu. Choose cd and the cd will boot. Obviously have the install cd in the drive when you start up. This is the ubuntu wiki entry for it [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)
If all goes right you start your computer with the install cd in the cd drive and the smart boot manager floppy in the floppy drive. Your computer boots to the SBM floppy which in turn boots you to the cd. The cd then runs the install. Hopefully[-o<

---


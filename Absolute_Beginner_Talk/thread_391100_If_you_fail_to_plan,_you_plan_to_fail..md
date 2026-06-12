---
title: "If you fail to plan, you plan to fail."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by TopHatCat on 2007-03-22
Having used Microsoft Operating Systems for the past 20 years I found that I wasn't learning anything new so I completely took the plunge, formatted my HDD, and installed Ubuntu 6.10 having very minimal prior Linux experience with Red Hat.

This was three weeks ago.

I've had numerous frustrations getting various aspects of hardware and software to work. Obviously having used MS-DOS for many years and being quite familiar with DOS command line interface it is pretty frustrating to be such a complete newb when it comes to any command line interface work with Linux.

**To make a long story short **- I want to use Ubuntu as my primary OS. No doubt about it. I've totally loved the whole community aspect of using an open source OS and the people I've met on this forum have been so helpful. I've still had great difficulty getting my wireless and video acceleration to function properly.

I want to re-format my HDD and install Windows XP on a 5GB partition, Ubuntu on a 20GB partition, and everything else on a [TrueCrypt]("http://www.truecrypt.org") partition.

While I want Ubuntu to function as my primary OS I still feel like I need Windows XP as a backup because I am totally familiar with it and I know that if I absolutely need to burn a DVD, download a torrent, or just use my wireless NIC that I won't have any problems with it.

At least until I'm ready to fully format the HDD again and be done with Windows forever. :)

**My questions: ** *1)* If I go home and format my HDD right now... should I install Windows XP first and Ubuntu second or the other way around?  *2)* Does anyone have any experience with 512bit encryption and Linux?

---

### Post by hardyn on 2007-03-22
windows first!  makes things easier.

no high encryption experience... i don't do anything security critical

---

### Post by goatflyer on 2007-03-22
Windows wants to be on the first partition, so install that first.  Ubuntu is happy anywhere else.  When you set up your dual boot system, grub (the bootloader) will still default to Ubuntu first.

---

### Post by huzzak on 2007-03-22
I'm pretty sure that the best order is Windows, then Linux.  I think that Linux takes care to not step on Windows' toes if you don't want it to but that Windows doesn't care much for the same.

---

### Post by Arby on 2007-03-22
In answer to question 1, I would always do Windows first and Ubuntu second. Windows does not play well with others and tends to make a mess of the boot menu if you install it second. Ubuntu is pretty good at detecting that you already have an existing OS on the disk and making sensible decisions about how to handle boot options.
You might find this wiki page helpful [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) also there are dozens of HOWTOs on these forums for doing dual boot if you search around a bit. Try the tips and tutorials section

No idea about 2 sorry.

Hope that helps

Arby

---

### Post by TopHatCat on 2007-03-22
So after I've installed XP and Edgy then Edgy should default to the primary boot partition without me having to do any kind of... special tweeking?

> no high encryption experience... i don't do anything security critical

Neither do I, but thats no reason for me not to learn it anyway. :) My job involves the encryption of entire networks and I'm proficient with that side of crypto but not so much with encrypting data volumes. I figure that if I learn that as well it will make me more marketable with all of my clearances and whatnot.

---

### Post by Arby on 2007-03-22
Yes, my understanding is that grub should default to boot Ubuntu for you. If it doesn't, investigate the contents of /boot/grub/menu.lst. That's the config file for the grub bootloader, you can set which system boots by default in there. It's pretty well commented but if you get stuck post the contents of the file here and let people have a  look at it.

EDIT: Another piece of advice. If you don't already, since you're doing a fresh install make a seperate partition for your ubuntu home directory. That way when you come to upgrade (or rescue if things go wrong) you can upgrade the OS and still keep your personal data files and settings.

---

### Post by TopHatCat on 2007-03-22
As always you guys are incredibly helpful. :)

If anyone has any input on the encryption issue feel free to pipe in. I think I'm gonna start formatting shortly after I get home today.

---


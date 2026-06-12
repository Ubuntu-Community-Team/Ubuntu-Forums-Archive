---
title: "support installation on EFI-BIOS ?"
date: 2007-04-24
forum: Apple Intel Users
---

### Post by tigerliu on 2007-04-24
hi:
does Ubuntu 7.04 supports installation on platform with EFI-BIOS?
I mean:
Installing Ubuntu 7.04 on EFI shell environment.
(If an OS supports it, then its iso image will have a hidden fat partition)

Thank you!
best regards!

---

### Post by oskarloko on 2007-04-27
Yes, there are a lot of us who have installed Ubuntu on Macbooks or iMac ( EFI ) without error.
The best method: use rEFIt and install Ubuntu on one of first four partitions ( compatibility with legacy MBR )


Also, you can use GRUB2 - PUPA or ELILO...  but that's more experimental

Serach ubuntu wiki for a howto

---

### Post by tigerliu on 2007-04-28
hi,oscarloko:
thank you for your reply!

But, i can not find a FAT partion in the ISO image on the EFI shell command environment.
(there should be an elilo.efi and other boot files on this FAT partition)

best regards!

---

### Post by ronocdh on 2007-04-29
> **tigerliu said:**
> hi,oscarloko:
thank you for your reply!

But, i can not find a FAT partion in the ISO image on the EFI shell command environment.
(there should be an elilo.efi and other boot files on this FAT partition)

best regards!
I still don't quite understand your issue. But if it helps, Feisty still isn't truly EFI-friendly; for example, my installation still stuck the GRUB info on my MBR (which was pre-existing from my WinXP installation). I personally use [rEFIt]("http://refit.sf.net") to triple boot my system. Choosing either Ubuntu or Win XP from the rEFIt boot screen just takes me to the same GRUB menu.

If this isn't the info you wanted, please restate your case.

---

### Post by Romu on 2007-04-30
I don't really understand your issue with EFI.

But I use Ubuntu on my Macbook Pro as a single OS (no windows no OSX, just Linux).

Edgy and Feisty can be both installed without any problem.

---

### Post by benanzo on 2007-04-30
I think the issue is not whether Ubuntu can be installed in an EFI environment, but if it can be installed without using the MBR.  I am wrestling with this myself.  I want to be able to use the GPT as the partition map without doing anything with the MBR.  There are only two bootloaders that I know of that can operate with GPT, GRUB2(formerly PUPA) and ELILO.

From my research I have figured out that on every GUID partition table (gpt) there is an MBR entry as the first block.  This is part of the spec from Intel to make EFI compatible with legacy bootloaders that require an MBR to boot their OS.  OS X will boot from an MBR but it wont install to anything other than a GPT.  You can get around this by installing it to a GPT disk, then cloning the partition and moving it to an MBR with a legacy bootloader.  GRUB can boot OS X even if it's not in an EFI environment then.

rEFIt uses a utility called gptsync that syncronizes the partition map between the GPT portion and the MBR portion so that everyone knows about everyone else and there are no surprises and no unbootable errors.

So, if you wipe the entire disk in your MacBook and install only Feisty today, you shouldn't get any errors at all.  The reason is because Apple updated the EFI firmware awhile ago that allows for limited BIOS emulation including writing an MBR to the disk.  GRUB will install to this MBR just fine and boot normally.  The only hiccup is that when you first power on your machine you'll have to wait at the grey screen for about 5 seconds and then see the folder with the ? in it (indication that it can't find a bootable disk) until it finally checks the MBR and sees you've got GRUB installed and then Feisty will boot.

I am trying to skip the whole MBR/BIOS emulation business and try to get GRUB2 or ELILO to run right in the EFI environment so that I get them to boot the same as if it were just OS X installed.  rEFIt is a great utility and if I were dual booting I would use it, but as of now I've just got Feisty installed and GRUB boots fine after that little wait I told you about.

If you have any ideas about ELILO and why the module efivars is not in Feisty so I can use efibootmgr to tinker with the EFI stuff, let me know.

---

### Post by Ptero-4 on 2007-05-04
I got a question. If you use GRUB2 or ELILO. Can you boot the machine from EFI (GPT) w/o rEFIt? Also are those bootloaders graphical (like GRUB) or text-based (like yaboot/lilo)? And if they´re text-based, are there plans to make them full graphical? if not, why?

---

### Post by benanzo on 2007-05-04
I am working on getting Ubuntu to boot in EFI mode with ELILO and/or GRUB2 via GPT without doing anything with the MBR or BIOS emulation.  As soon as I have a breakthrough I'll post it here first.

---

### Post by cabdouch on 2007-12-03
My MacMINI has the CSM module in it, so Linux installs in the Legacy mode and isn't EFI aware.
I assume older Intel MACs don't have the CSM and have a more EFI Only BIOS.
This seems to be what most people in these postings are talking about.

Meanwhile, I am working on a team developing a EFI Only BIOS for a Intel 945 based system.
Through that experiance I relate to the questions and problems here.

As to the original poster (tigerliu) of this thread asking about an EFI Only Install method, I posted the following thread:
[http://ubuntuforums.org/showthread.php?p=3886557#post3886557](http://ubuntuforums.org/showthread.php?p=3886557#post3886557)

Benanzo, I known exactly what you're talking about and posted some info to:
[http://ubuntuforums.org/showthread.php?t=213793](http://ubuntuforums.org/showthread.php?t=213793)
As well as your earlier thread:
[http://ubuntuforums.org/showthread.php?t=426566](http://ubuntuforums.org/showthread.php?t=426566)

As I learn more, I will try and follow up post to your questions.

Looking at the source code for efivars, it claims to look for the EFI System table at a hard-coded address instead of using the address passed into elilo from the Boot Manager. I don't know if it really does this, but that is what the comments say.

If so, chances are that Apple as well as my own BIOS have the table elsewhere and efivars hangs when it "calls" the hard-coded location.

---

### Post by cyberdork33 on 2007-12-03
> **cabdouch said:**
> My MacMINI has the CSM module in it, so Linux installs in the Legacy mode and isn't EFI aware.
I assume older Intel MACs don't have the CSM and have a more EFI Only BIOS.

If you want to boot from EFI, you have to build an EFI able kernel and use elilo / grub2.

---


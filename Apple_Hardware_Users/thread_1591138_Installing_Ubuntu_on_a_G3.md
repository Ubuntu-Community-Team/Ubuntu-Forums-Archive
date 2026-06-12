---
title: "Installing Ubuntu on a G3"
date: 2010-10-08
forum: Apple Hardware Users
---

### Post by k3lt01 on 2010-10-08
Hi.

I had better preface this thread by saying I know nothing about Macs so this is a HUGE learning experience for me.

A few weeks ago I was given an old G3 server, the one with the snazzy blue case with the drop down side, to refurbish and do whatever I wanted with as I do up old PCs and give them away. The original disk in the machine has OS 9 installed and I was also supplied with the OEM OS 8 server install disks.

The machine has a SCSI card connected to a 9GB hdd. I have plenty of normal hdds laying around so I fitted one and installed OS 8 onto it to see things were as thy should be. It installed fine. I then put in another disk and attempted to install 10.04 and it wouldn't even see the hdd (I know its a good on as I have since used it in another PC I refurbished). I then fitted a 200 GB SCSI drive (I have 2 of these and tried both) and attempted to install 10.04 on it.

Now this is where the fun starts. First the system only sees 40 GB of the available 200 GB, and second when I get to the partitioning it asks me what driver do I need to install for my hdd showing me a list of available drivers. I have been through the list and tried every one of them but am unable to get any further than this step.

This leads me to my questions.
Is there some trick to Macs when installing Ubuntu?
Why won't it recognise a regular hdd drive?
Why won't it recognise all 200 GB of the SCSI hdd drive?
Why is it asking for a driver for the SCSI hdd? and how do I know what one it needs?
I'd really like to get this thing working but I think I'm going to need your help. I can work my way through an IBM clone (to use an old terminology) with no difficulty but I have always had difficulty with Apple/Macs even with just regular usage.

Thanks in advance.
Michael.

---

### Post by MisterGaribaldi on 2010-10-09
Oooooooooh...

Unfortunately, the Mac you've got is now about 12 years old. It isn't just so much a function of age as much as it's a combined function of age plus CPU architecture plus manufacturer (un)willingness to support their hardware on any other OS besides their own.

If you just want to use it as a server, then I'd strongly recommend you go with Debian. They currently support 11 different architectures, including PPC.

You need to dial down whatever expectations you have. PPC is NOT well represented in a number of areas, such as 3D graphics card drivers, sound, Flash, etc. If you're trying to use it as a desktop, then you would be far better served getting a Mac OS 9.1 install CD for it and using that to do a nuke-n-pave and start with a fresh setup.

Vis a vis your various hardware comments, remember, that's a 12 year old system. Everything in the world has since 1.) abandoned SCSI (apart from specialized server-type systems) and 2.) also abandoned IDE in favor of SATA.

Your best bet is to check out support.apple.com for more specific info on what the limits are for supported hard drive capacity. You might want to check with places such as MacSales or ShreveSystems because they both do a good business trade in supporting older Mac hardware.

Good luck!

---

### Post by k3lt01 on 2010-10-09
Thanks for your reply.

I thought it would be fairly old.

Due to the fact that I do this as a voluntary service I can't (read wont) even consider engaging the paid services of a technician. If I can't get Ubuntu (or Debian, thanks for that suggestion) to install I'll just scrap the machine.

I found an Ubuntu wiki page discussing "Old World" and "New World" Macs and I think this thing may be an "Old World" Mac.

I am open to any suggestions.

---

### Post by MisterGaribaldi on 2010-10-09
> **k3lt01 said:**
> Thanks for your reply.I found an Ubuntu wiki page discussing "Old World" and "New World" Macs and I think this thing may be an "Old World" Mac.

I am open to any suggestions.

Nope, it's a NewWorldROM Mac.

The system it replaced, the "beige" G3 Desktop / Tower range, and any other system of that generation or older, are OldWorldROM Macs.

All iMacs (even going back to the first one in 1998 ) all "bondi blue" Blue-and-White G3 towers, and all G4 systems period and newer, up to but not including any x86-based systems, are NewWorldROM systems.

OldWorldROM systems, by comparison, cannot "boot" anything other than an Apple-produced OS and therefore require BootX to circumvent this by booting into Mac OS and then loading a Linux RAMdisk file and kernel into memory, then basically purging everything else and switching over to the pre-designated partition. It's a fairly crude hack, but it worked.

NewWorldROM systems can boot into any OS that supports the hardware, and make use of the Yaboot boot loader to do this.

But then, why bother with Linux in the first place? Unless you're making this thing into a server, you're far better off putting a fresh install of Mac OS on it. At least you can take full advantage of the hardware.

---

### Post by oswaldkelso on 2010-10-09
Don't waste your time trying a full Ubuntu install on hardware that old. Or using Mac OS unless you don't use the internet or share documents. It's to old to be of real use. OSX if it would install would crawl. 

Read the old imac how to in my sig first to get you started, it's out of date but has lot's of info and clues in it. 

Up date the firmware first this can only be done from Mac OS

I would do a minimal install and build my system with openbox and rox-filer. It's more work but you have system that's up to date, easy to use, pretty and as quick as your going to get with a gui. If the end user would need a more familiar DE you could go for a minimal LXDE install and build the system from the ground up. Once done your granny could use it.

Debian offers better PPC support than Ubuntu so if you want an up to date OS on old hardware that's the way to go. 

If you want the easy option and just grab the xfce+lxde iso 

[http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso) 

Then after you've installed make sure your sources.list says squeeze and not testing, as there maybe a whole load of bugs hitting testing when squeeze goes stable.
 
Check your machine spec here:
[http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html](http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html) 

You'll need at least 256mb of ram more is better but I find 512mb is plenty.

Have fun.

---

### Post by k3lt01 on 2010-10-09
Thanks for that Oswald. Brilliant write up in your link. I appreciate the effort that went into it.

I'll take a look at Squeeze and see how I go from there. This may take some time as today is the Bathurst 1000 (I am most certainly going to sit and watch it, no Commonwealth Games today for me) and tomorrow I start a new job. I shall refer back to your HowTo if I come across any issues and post here if I can't find answers.

Thanks again.

---

### Post by Compgeke on 2010-10-10
You asked why the iMac won't see all 200 Gb. of a hard drive. This is because of lack of support for 48-bit LBA. The iMac won't work with any hard drive larger that 128 Gb.

---

### Post by linuxopjemac on 2010-10-10
I can also recommend my own MintPPC 9. You can install it from a Debian base installation.
[http://mac.linux.be/content/mintppc-9-released](http://mac.linux.be/content/mintppc-9-released)

---

### Post by oswaldkelso on 2010-10-10
> **Compgeke said:**
> You asked why the iMac won't see all 200 Gb. of a hard drive. This is because of lack of support for 48-bit LBA. The iMac won't work with any hard drive larger that 128 Gb.

The approx 8gb limit on older imac (233-333 mhz) and 128gb limit on other mac models is only in regard to the OS. You need to partition your drive so the first partition with the OS is under the size limit. Then it will install and you can still use the extra space of your larger drive as storage.

If you dual boot. Both OS's need to be installed within the 8gb or 128gb limit.

---

### Post by jimwg on 2010-10-10
I've a 900mHz G3 iBook running on three partitions Ubuntu 10.04, Tiger 10.4.11 and 1.3.9 and the PPC sides run smoothly, so it can be done on a G3. It was more tedium than difficult getting the Ubuntu partition set-up, but it ran great until I started "experimenting" with Ubuntu like trying to rename a second user account in Terminal which now crashes any access to it from my main account and completely killed the Users and Groups function, but otherwise it runs okay and hopefully someone over at Launchpad Ubuntu can give me clues to undo that mistake. Regrettably, Ubuntu won't write to my Mac partitions, and won't go wireless on-line by refusing my password as "Bad Password" even though I CAN go on-line if I nix password from my eMac server, but going wireless online "unsecured" like that makes me feel naked to wolves in the dark. I have a funny feeling Ubuntu 10.10 misreads WEP passwords coming in because this never happened under 9.04. Hopefully I can open an issue here about this if it's not redundant. Everyone here is a fountain of info I've always been grateful of!

Jim

---


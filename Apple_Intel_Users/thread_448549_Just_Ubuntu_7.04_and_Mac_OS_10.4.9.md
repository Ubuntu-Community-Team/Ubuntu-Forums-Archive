---
title: "Just Ubuntu 7.04 and Mac OS 10.4.9"
date: 2007-05-19
forum: Apple Intel Users
---

### Post by l0rdn1k0n on 2007-05-19
(MacBook 1st gen 1.83 GHz Core Duo with default 512MB RAM)

I've tried using Ubuntu through a live cd, but it wouldn't boot on an intel mac and won't install either. I've tried using parallels, but with the default 512 MB of RAM and incredibly sluggish results I'm at my wit's end here. I have just finished downloading the installer for Boot Camp, and am currently downloading the installation ISO for Ubuntu 7.04. This is what I would love to do:

 Use Boot Camp boot menu (holding option at boot) and select between Ubuntu and Mac OS X. I DO NOT have, nor want, Windows XP/Vista etc.

Now the reason I want to use the Boot camp method is that it can partition my HD without deleting my data (I still have NO IDEA how it does that, but somehow it does). I do have backups, but it would still be a hassle to go through and reinstall everything; especially the hundreds of 50+ MB  security updates from Software Update...that alone is worth avoiding.

My experience with partitions: I screw them up. It's that simple. I can't figure out how to partition the drives, especially since linux needs two partitions to run doesn't it? And I dunno how to do that AT ALL. Consider me a partition noob.

I have installed a Linux OS before on a Dell I used, but I just used the entire hard disk for Ubuntu because I didn't want Windows. Now, I need to make sure to install on the correct partition, and that's where somebody with a LOT of understanding in this dept. comes in. I am sure somebody has tried this before (successful or not) and I would appreciate either a link to a tutorial or perhaps somebody could guide me along via AIM (in my profile) and that would prevent me from destroying my lovely MacBook.

If you're wondering, I need Ubuntu for software development that requires the tools only found on a linux machine. Unfortunately. Plus I love the idea of having a choice. :)

For those who don't like to read a lot (myself included):
I need to install Ubuntu 7.04 Feisty Fawn on a MacBook using Boot Camp. If I can't use boot camp (which would still be OK, just something I'd prefer) I would like to have the ability to dual boot and use a boot loader (any as long as i can choose between the two at startup).

Thanks in advance for anybody who posts!
-l0rdn1k0n

---

### Post by ronocdh on 2007-05-19
This is a pretty trivial process, now that Feisty's out, you'll be happy to hear! First you want to download the ISO from Canonical's website. You can grab the i386 build, which is a 32-bit version compatible with both the Core Duo and the Core2 Duo Mactels, but with a Core2 Duo you also have the option of 64-bit. If you have a C2D, I recommend the 64-bit version (called "AMD64"), as you'll get better performance out of your hardware.

Alright, so you've created a second partition in Boot Camp already, yes? Once that's done, exit the Boot Camp utility and reboot your computer with the Ubuntu Live CD in the drive. You can hold down the C button to boot from the CD, or, if you have [rEFIt]("http://refit.sf.net") installed, it'll prompt you automatically. Either way, once the the main menu of the CD appears, choose **Check CD for errors**. This is a checksum verification process that is very important, because you don't want to be trying to install with a poorly burned CD!

I'll take this time to mention that you shouldn't be creating the CD with any application other than **Burn**, which is available [here]("http://www.opensourcemac.org"). It automatically verifies the integrity of the disc after burning.

Then, once you know your CD is good, proceed with the installation. Leave your OS X partition untouched, of course, then assign your other partition to Ubuntu. Do NOT assign swap space. The installer will ask you about this, raising its eyebrow at you, but assure it you know what you're doing and then sit back while the installer runs (can take 30-40 minutes). When it's finished, you'll be asked to reboot and remove the CD.

If you do not install rEFIt, I believe you'll have to hold down the Option key while booting to see the OS selection menu. I like rEFIt because it's prettier, so if you feel like trying it out, download it for OS X and install the package it provides, then reboot.

I think that's pretty much everything you'll need to know for the installation. Post back with anything else, and good luck!

---

### Post by l0rdn1k0n on 2007-05-19
OK i have the Core Duo (not Core 2 Duo), so i downloaded the default x86 installer (32bit) from the actual ubuntu website. is there any difference between the ISO on ubuntu's site or canonicals? they look like the same thing. and i haven't partitioned using boot camp yet, the only question i have is when i do boot the ISO and click the install icon, will the name's i assigned to my hard drive (Macintosh HD) show up or will it be /dev/hda1 and /dev/hda2? if it's the latter I won't know which one to use. But I do get to decide the size so I can use that to determine it now that I think about it :lolflag: but ya, other than that I want to know if i can burn the ISO to a CD-RW so i can reuse the disc later. will computers boot from ISOs burned to CD-RW?

thanks again
l0rdn1k0n

---

### Post by ronocdh on 2007-05-19
> **l0rdn1k0n said:**
> OK i have the Core Duo (not Core 2 Duo), so i downloaded the default x86 installer (32bit) from the actual ubuntu website. is there any difference between the ISO on ubuntu's site or canonicals? they look like the same thing. and i haven't partitioned using boot camp yet, the only question i have is when i do boot the ISO and click the install icon, will the name's i assigned to my hard drive (Macintosh HD) show up or will it be /dev/hda1 and /dev/hda2? if it's the latter I won't know which one to use. But I do get to decide the size so I can use that to determine it now that I think about it :lolflag: but ya, other than that I want to know if i can burn the ISO to a CD-RW so i can reuse the disc later. will computers boot from ISOs burned to CD-RW?

thanks again
l0rdn1k0n
I recommend CD-R, just because it would be nice to have the disc handy at a later point in time, perhaps for a recovery or something. Don't mean to scare you, but I think it's something you should keep in your arsenal. I mean, CD-Rs are like 20 cents these days, so I would just burn it, use it, then tuck it away in a CD case somewhere.

Ubuntu/Canonical site distinction doesn't matter, it sounds like you've gotten the right ISO. Your partitions will certainly be referred to as /devs, but you're right about the sizes being a dead giveaway. Also, the installer should display the filesystems, too, so probably your Ubuntu partition will initially be FAT32, which you'll want to change to ext3 during installation. Your OS X partition will probably be listed as HFS+, though there's a chance it'll be "unknown." Either way, the sizes should let you know.

---

### Post by l0rdn1k0n on 2007-05-19
> **ronocdh said:**
> I recommend CD-R, just because it would be nice to have the disc handy at a later point in time, perhaps for a recovery or something. Don't mean to scare you, but I think it's something you should keep in your arsenal. I mean, CD-Rs are like 20 cents these days, so I would just burn it, use it, then tuck it away in a CD case somewhere.

Ubuntu/Canonical site distinction doesn't matter, it sounds like you've gotten the right ISO. Your partitions will certainly be referred to as /devs, but you're right about the sizes being a dead giveaway. Also, the installer should display the filesystems, too, so probably your Ubuntu partition will initially be FAT32, which you'll want to change to ext3 during installation. Your OS X partition will probably be listed as HFS+, though there's a chance it'll be "unknown." Either way, the sizes should let you know.

thanks very much you've helped me out a lot! :D

i'll post back by the end of the day when i've installed - gotta get a cd sleeve and some blank CD-Rs lol

---


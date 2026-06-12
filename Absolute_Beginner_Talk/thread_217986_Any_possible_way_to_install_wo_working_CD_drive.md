---
title: "Any possible way to install w/o working CD drive?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Araelius on 2006-07-17
Just as the title states, I am curious if there is any way at all to install Unbuntu without having and operational CD drive. I did acquire the laptop a while ago for free but the drive failed shortly after. It does not have a floppy drive and the hard drive is a mere 6GB, but I am hoping that there is some possible way to get Ubuntu or Xubuntu working. 

Anyway, any info is appreciated and if you have any questions, please feel free to ask. Thanks again.

---

### Post by deadgobby on 2006-07-17
> **Araelius said:**
> Just as the title states, I am curious if there is any way at all to install Unbuntu without having and operational CD drive. I did acquire the laptop a while ago for free but the drive failed shortly after. It does not have a floppy drive and the hard drive is a mere 6GB, but I am hoping that there is some possible way to get Ubuntu or Xubuntu working. 

Anyway, any info is appreciated and if you have any questions, please feel free to ask. Thanks again.
You can try netboot
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by Araelius on 2006-07-17
I am assuming that no answer means a no? Oh well, just gotta replace it I suppose.

---

### Post by Sef on 2006-07-17
> I am assuming that no answer means a no? Oh well, just gotta replace it I suppose.

From the site that deadgobby has a link to:

> Netboot Install

This HOWTO describes the steps required to start an installation of Ubuntu over the network (if you have e.g. an old machine with a non-bootable CDROM). 

---

### Post by Araelius on 2006-07-17
Thanks, it seems he posted the same time as I posted my second message :)

---

### Post by Araelius on 2006-07-17
I am skimming through the installation notes very quickly, but does this method require a bootable floppy drive, as I have stated the laptop does not have one available.

EDIT: Also, I will be attempting this via a WinXP computer if that would make any difference.

---

### Post by Araelius on 2006-07-18
Would installing a small linux distro such as Damn Small Linux or Puppy Linux be possible with only the use of a USB flash drive?

---

### Post by bernied on 2006-07-18
It looks to me like that netboot option needs another machine running linux (which you don't have, right?)

If you can boot to usb (not always possible) and you can make a bootable DSL or puppy usb stick, then you might try the following:

(but this is not a quick project and I don't recommend any of it if it's your first linux install)

- there's a package in debian called debootstrap that, once unpacked, gives you a (very) basic install, which includes apt-get. So if you have an internet connection, you can complete the installation over the web.

- the only (big) trouble you might have with this was that you needed dpkg to install debootstrap (which seems a bit dumb to me). I was doing this as a network boot install onto a gentoo machine, so it was easy for me to install dpkg, even though it's not part of the gentoo system. This might not be so easy for you to add dpkg to DSL or puppy. If this is a problem, a possible solution might be to get the DSL or puppy going, then share the laptop hard-drive (you would need nfs to be working), then do the work from a ubuntu live-cd on the computer that normally runs XP (assuming that a ubuntu live-cd has dpkg installed on it).

All this can also be done in gentoo, by installing a stage-3 tarball (you would still need the bootable usb stick to get started). Like the Debian debootstrap, this gives you a working system (except for the kernel, which you have to compile yourself). Gentoo is generally not considered suitable for beginners, and it will take longer on your old machine because everything is compiled from source, but it might possibly be easier in your case. 

You might find another solution around this general principle - download a zipped-up basic system that includes a method for installing a more complete system.

There is not much detail written here, but you will need lots of detail - there are many things that 'just work' in a normal ubuntu install that will not work using these methods and you will have to solve each of them as they arise. Not that you should be scared off, just be prepared for a steep learning curve and things taking longer than first expected.

---

### Post by bernied on 2006-07-18
And yes, if you can get DSL or puppy on a bootable USB stick, and you could boot the laptop onto it, then you could install the DSL or puppy onto the hard-drive. (I was going to write something here about why you shouldn't but it might start a bit of a flame-war. Let's just say they were designed as live-cd distributions, not for full-time use.)

And you might also consider slax as a usb install - it's very adaptable using the 'rootcopy' folder.

---

### Post by SkyNet2029 on 2006-07-18
In the 'MyDSL' section of the DSL archive is an app for adding Dpkg functionality to DSL.

---

### Post by RRS on 2006-07-18
It's still early in a.m. for me so I could be wrong here, but if the BIOS allows booting from a USB stick wouldn't you also be able to use a USB cd drive?

---

### Post by daller on 2006-07-30
> **RRS said:**
> It's still early in a.m. for me so I could be wrong here, but if the BIOS allows booting from a USB stick wouldn't you also be able to use a USB cd drive?

That goes for 99,9%!

It would be far easier to install from an external cdrom, instead of a USB-stick!

Anyway, I saw this post because I was searching for a way to install "Kubuntu 6.06 LTS" from a USB-stick!

Any ideas?

---


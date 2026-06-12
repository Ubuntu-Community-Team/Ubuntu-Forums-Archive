---
title: "3-way booting with yaboot questions"
date: 2007-10-03
forum: Apple PPC Users
---

### Post by garlicsalt2 on 2007-10-03
Ok, so I recently obtained a Blue and White G3. This is not my first Mac, my newest one before that is a 6100/60. This is my first "New World" Mac.

The Mac had OS 9.2.0 pre-installed. Since someone had given me an OS X 10.2 "Jaguar" disc set, I loaded that on top of OS 9. I then changed that drive to IDE slave, and put in another HDD, and loaded Ubuntu Dapper, which I had received from shipit/canonical.

Well, I can dual-boot, but I cannot boot into OS 9, without problems. If I put in macos=/dev/hdX# into yaboot.conf, I still get OS X when I select it.

My apologies for not including logs and config files, as I am booted into OS X currently, and do not have this info in front of me.

I did read in the yaboot.conf man pages about a "nobless" option, but I am unclear as to how to use it, or if it is even needed in my case.

I will follow-up, on request, with my *yaboot.conf* file and/or output of "**fdisk -l**"

Also, while I on the topic of yaboot.conf, is there any way to specify a removable disk as a boot source, such as a usb or firewire drive, or a zip disk?

Thanks,
--Aaron

---

### Post by pxwpxw on 2007-10-05
> **garlicsalt2 said:**
> Ok, so I recently obtained a Blue and White G3. This is not my first Mac, my newest one before that is a 6100/60. This is my first "New World" Mac.

Well, I can dual-boot, but I cannot boot into OS 9, without problems. If I put in macos=/dev/hdX# into yaboot.conf, I still get OS X when I select it.


Have you run
```

sudo ybin -v

```

This updates the boot files from /etc/yaboot.conf
(see man ybin)

---

### Post by grazie on 2007-10-05
> **garlicsalt2 said:**
> 
Also, while I on the topic of yaboot.conf, is there any way to specify a removable disk as a boot source, such as a usb or firewire drive, or a zip disk?


Yes there is, but I think I'm correct in stating that the B&W PowerMac is the only New World Mac that cannot be booted from an external source.

---

### Post by garlicsalt2 on 2007-10-05
> **pxwpxw said:**
> Have you run
```

sudo ybin -v

```

This updates the boot files from /etc/yaboot.conf
(see man ybin)

Well, sort of. I ran the ybin program after modifying /etc/yaboot.conf, but not with the "-v" parameter. I won't ask the purpose of this command line argument, 'cause I can get the answer from the man pages, or even by running it, before an answer would likely arrive arrive.

---

### Post by pxwpxw on 2007-10-05
> **garlicsalt2 said:**
> Well, sort of. I ran the ybin program after modifying /etc/yaboot.conf, but not with the "-v" parameter. I won't ask the purpose of this command line argument, 'cause I can get the answer from the man pages, or even by running it, before an answer would likely arrive arrive.

-v verbose

please post 
```

 cat /etc/yaboot
 sudo mac-fdisk -l

```

---

### Post by garlicsalt2 on 2007-10-07
Okay, that's weird. I posted a reply last night, with the requested output, plus the output of ybin -v, for good measure. Oh, and I had guessed that '-v' was verbose., but I didn't want to say untill I knew for sure. There is an exception to every rule, except this one! :p

I'll try to follow-up tonight, with the requested info.

Trying to do anything with 10.2, just isn't easy anymore. I may break down and buy 10.4, and download Ubuntu Gutsy Gabon when it is released, and reinstall.

---

### Post by walter_f on 2007-10-08
> **grazie said:**
> Yes there is, but I think I'm correct in stating that the B&W PowerMac is the only New World Mac that cannot be booted from an external source.

There's also the first generation of the Power Mac G4 (with PCI graphics, a.k.a. "Yikes") in which one should not take booting from a Firewire drive for granted. The architecture in this series shares more features with the b&w G3 than with the following PM G4s.

Starting with the following Power Mac G4 generation (AGP graphics, a.k.a. "Sawtooth") and later, booting from a Firewire drive is no problem, of course.

Walter.

---


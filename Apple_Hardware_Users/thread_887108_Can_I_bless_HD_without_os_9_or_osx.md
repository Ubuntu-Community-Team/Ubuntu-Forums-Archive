---
title: "Can I bless HD without os 9 or osx?"
date: 2008-08-11
forum: Apple Hardware Users
---

### Post by balebozb on 2008-08-11
Hi Guys,
I've installed another hard drive from a PC. I've installed both YDL 5.0.2 and Feisty Fawn with no problems, but all I get is the flashing-question mark folder at start-up. I've seen that I need to bless the HD, but I don't have os 9 or osx disks. Is there a way around this? I can boot the Feisty Fawn live OK. Any help will be appreciated.
Thanks,
Balebozb:confused:

---

### Post by cyberdork33 on 2008-08-11
What Mac are you on? Intel or PowerPC?

---

### Post by estyles on 2008-08-11
(post deleted - I guess the bump wasn't appreciated...  =) )

---

### Post by cyberdork33 on 2008-08-11
> **estyles said:**
> Bless the HD?  Is that seriously a thing?  I think you may need a bishop for this one.
If you have any relevant information that would be helpful.
[http://www.manpagez.com/man/8/bless/](http://www.manpagez.com/man/8/bless/)

---

### Post by Ptero-4 on 2008-08-11
> **estyles said:**
> (post deleted - I guess the bump wasn't appreciated...  =) )
Blessing a disk is the PowerPC equivalent of changing the boot order in the BIOS for us PC users (this is because PowerPC´s didn´t use a BIOS, they use a custom sort of firmware called "open firmware") also the OP needs before using the bless command to convert the partition table to the PowerPC compatible (he said he took the HD from a PC so likely it´s partitioned in the DOS style format which gparted can use and can even be used as storage on his Mac, but won´t work as boot device until he converts it´s partition table to Mac).

---

### Post by cyberdork33 on 2008-08-11
> **estyles said:**
> (post deleted - I guess the bump wasn't appreciated...  =) )
I simply gave you some information about what the OP was referring to, and asked that you share any information you might have.

> **Ptero-4 said:**
> Blessing a disk is the PowerPC equivalent of changing the boot order in the BIOS for us PC users (this is because PowerPC´s didn´t use a BIOS, they use a custom sort of firmware called "open firmware") also the OP needs before using the bless command to convert the partition table to the PowerPC compatible (he said he took the HD from a PC so likely it´s partitioned in the DOS style format which gparted can use and can even be used as storage on his Mac, but won´t work as boot device until he converts it´s partition table to Mac).On the other hand, if it is an Intel Mac, you can bless it still :)

---

### Post by estyles on 2008-08-12
> **cyberdork33 said:**
> I simply gave you some information about what the OP was referring to, and asked that you share any information you might have.

On the other hand, if it is an Intel Mac, you can bless it still :)

Okay, I took it as a semi-reprimand, and since I totally was just being silly in a serious support thread, that was my way of apologizing... ;)  IMHO, that command is totally sacrilegious, and if I were a fundamentalist, I'd probably refuse to use Apple hardware on that principle alone, but since I'm not, I manage to find other reasons... 

Anyway, the two of you seem to have helped the OP out, so my work here is done.

---

### Post by balebozb on 2008-08-12
I'm using an iMac g3 400 DV, I appreciate any help on this. 
Thanks,
Balebozb:confused:

---

### Post by cyberdork33 on 2008-08-12
> **balebozb said:**
> I'm using an iMac g3 400 DV, I appreciate any help on this. 
Thanks,
Balebozb:confused:
In that case, Ptero-4 has the best advice here.

---

### Post by balebozb on 2008-08-14
I'm sorry: I'm a newbie to Apple with LInux, so I don't even know where to start. Can someone please give me some pointers?:confused:

---

### Post by cyberdork33 on 2008-08-14
I am not a ppc user, but I think that ybin can bless.

---

### Post by balebozb on 2008-08-14
I have no idea how to do that. Can you give me some pointers? I've always just installed Ubuntu and other linux distros on PC's.:confused:

---

### Post by pxwpxw on 2008-08-15
> **balebozb said:**
> I have no idea how to do that. Can you give me some pointers? I've always just installed Ubuntu and other linux distros on PC's.:confused:

You need to find out what you have got there.

Use your linux live cd and in a terminal get the G3 boot-device and the disk partitioning info.

```

$ sudo nvsetenv boot-device
$ sudo mac-fdisk -l

```

Post the result (if any).

---

### Post by screwballl on 2008-08-15
I have Kubuntu 6.06 on my iMac G3... I cannot get any newer version of Linux to work on it so it stays with what it has.
Support for PPC in Linux has dropped off since the advent of IntelMacs and I found that 6.06 LTS is the last full supported version of Ubuntu that actually works well.

---


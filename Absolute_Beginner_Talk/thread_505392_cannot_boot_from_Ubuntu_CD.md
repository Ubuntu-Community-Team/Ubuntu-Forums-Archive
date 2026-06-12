---
title: "cannot boot from Ubuntu CD"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by spacedboy2k on 2007-07-20
hi,

My computer runs with Pentium 4. It has WinXP and Mandrake Linux 10.1 installed. 

I downloaded the i386 image file. MD5 hash values check out ok. I extracted the files from within the image file and burned them to a DVD. The Ubuntu CD comes up ok from within Windows. Now I want to install Ubuntu. The problem is that it doesn't come up on boot. Even selecting the CD drive as the boot source doesn't help. The computer tries reading from the CD drive and then goes directly to the usual options (Windows or Mandrake Linux). 

Any ideas on how to solve this? Could it be something to do with LILO?

---

### Post by Skrynesaver on 2007-07-20
Does your dual boot use LILO?
If it's using grub you could force it to boot from the CD 

Assuming the cd is the second device on the first IDE controller:
```

grub>root (hd1,0)
grub>kernel /vmlinuz root=/dev/hdb1 ro
grub> boot


```

---

### Post by spacedboy2k on 2007-07-20
Yes, it's using LILO, so I can't try what you suggested. Thanks for the reply, though :)

---

### Post by ddrichardson on 2007-07-20
*>> I extracted the files from within the image file and burned them to a DVD*

Create a disc from the ISO image rather than creating a DVD with the extracted contents - that's why it isn't bootable.

---

### Post by davidjmayo on 2007-07-20
> I extracted the files from within the image file and burned them to a DVD.

Burn the Cd as .iso. Do not extract the files.

A burning guide here if you need it
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ddrichardson on 2007-07-20
It freaks me out a little when two people at other ends of the world come to the same conclusion at the same time! ;-)

---

### Post by spacedboy2k on 2007-07-20
Tried that. Doesn't work, not even when I select the CD drive as the boot source.

---

### Post by ddrichardson on 2007-07-20
Do you have any other bootable CDs? If so try them to confirm its not this image thats at fault.

Second, does your BIOS have any settings that alter the boot sequence order?

It's not to do with LILO because the BIOS hands over to LILO on the MBR after determining the primary boot device.

---


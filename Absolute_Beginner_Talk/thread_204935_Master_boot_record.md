---
title: "Master boot record"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by scurtish on 2006-06-27
I booted a copy of Ubuntu 6.04 to try it. But now I find that I can't 
start Windows XP without having the Ubuntu CD in the drive, and then
select boot from hard disk.

I've tried booting the computer with the XP CD going into the Recovery Console, and then running FIXMBR, but the computer still will not boot to Windows
without the Ubuntu CD inserted.

Any ideas?

Thanks

---

### Post by Sonofmoog on 2006-06-27
We need more information.  

1) How are you booting?  Is this a standard Windows XP boot where Drive C: is active?

2) What *specific* error message are you getting?

3) There is no other operating system on the hard drive besides XP.  Is this correct?  

4) What is the boot order in your BIOS?


Things to try:

Try booting from the XP Menu.  As the computer boots, tap the F8 key until you see the XP boot menu.  Select normal boot first and if that doesn't work, select safe mode

Put in a blank CD in the CDROM drive, then try rebooting

Try disabling CDROM boot in the BIOS and boot from floppy and hard drive only .. 

I'd also recommend that you Google for "Windows XP" "boot disk" "how to"  Your first hit should be the Microsoft Knowledge Base article on how to make an XP boot disk.  Make it, then try booting from it .. 

If none of these work, come back and we'll likely have more things for you to try.

---

### Post by masterjonny on 2006-06-27
Things to try continued:

Once you have booted with the bootdisk use the "fdisk" command to make sure you Windows partion is flagged as bootable

---

### Post by Jagot on 2006-06-27
Another possibility is to use a FreeDos boot disk - [http://www.freedos.org/](http://www.freedos.org/) - to restore the MBR.  That would need you to type this at the prompt:

```
fdisk /mbr
```

---

### Post by scurtish on 2006-06-28
Thanks to all those suggesting fixes to the problem. I found the problem and all is well at this point. Not sure how it happened, but BIOS settings got a bit messed up. My boot order was CDROM, HDD-1. There is no HDD-1 in my system, and the original BIOS settings that I had a backup up of, showed the boot order being CDROM, HDD-0.

---


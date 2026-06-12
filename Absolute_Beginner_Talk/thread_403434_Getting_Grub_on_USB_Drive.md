---
title: "Getting Grub on USB Drive"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by mwf on 2007-04-07
I installed Ubuntu 6.10 on an external USB hard drive. However, the last step, installing grub on the external drive failed (I want to boot directly from the USB, no C drive involved). I tried entering "sda", "(sda)", "sda1", (sda1)" at the grub graphical prompt all with the same results, a failure. The boot/grub directory is there but it doesn't have any menu.lst or any other files.

I am installing from the Live CD.

Without another Linux box around, how do I make this external USB hard drive a Ubuntu-bootable drive? 

mike

---

### Post by confused57 on 2007-04-07
> **mwf said:**
> I installed Ubuntu 6.10 on an external USB hard drive. However, the last step, installing grub on the external drive failed (I want to boot directly from the USB, no C drive involved). I tried entering "sda", "(sda)", "sda1", (sda1)" at the grub graphical prompt all with the same results, a failure. The boot/grub directory is there but it doesn't have any menu.lst or any other files.

I am installing from the Live CD.

Without another Linux box around, how do I make this external USB hard drive a Ubuntu-bootable drive? 

mike
You need to use **/dev/sda** to install grub to your external drive mbr, if that's your USB drive.

Your external drive should be set to boot before your internal hard drive in bios, before installing Ubuntu.

---

### Post by mwf on 2007-04-07
Thanks, that worked. Now if I could just get the thing to actually boot of the external drive!

---

### Post by Gina on 2007-04-07
If you can set the bios to boot from the external drive I would have thought that would have worked.  Unfortunately my PCs don't have that available or I'd do the same.

---

### Post by mwf on 2007-04-07
> **Gina said:**
> If you can set the bios to boot from the external drive I would have thought that would have worked.  Unfortunately my PCs don't have that available or I'd do the same.

Yeah, I thought that too! Unfortunately, the computer churns around for a while and then does a normal boot from the internal drive. I have played with menu.lst, including making the wait time 30 seconds to allow the USB system to load, but nothing. I also changed the boot drive names in the file but nothing.

Linux takes a lot more effort to get going, definately not an install for the faint of heart. I am playing with the idea of buying the new Mandriva 4G USB key that is allegedly set up to boot correctly right out of the box. The school is taking a preliminary look at Ubuntu (second attempt in a year) and no one is happy that can't do more than a live CD!

---


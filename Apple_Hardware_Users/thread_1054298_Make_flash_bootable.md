---
title: "Make flash bootable"
date: 2009-01-29
forum: Apple Hardware Users
---

### Post by Jaiibee on 2009-01-29
God, I know this has probably been asking hundreds of times before and my epic researching abilities have proven their efficiency, but how exactly do I make my 4GB imation USB bootable using my Mac OS X 10.4 PPC?

I do NOT want to boot from my Mac (which is what i mostly get on gooogle), I want to make a flash drive bootable so I can actually install an OS onto my USB.

I've tried doing that disk utility and i'll try again, but please help me if you know how.

Edit: Got an "error 6, destination not configured" or something

---

### Post by dank28 on 2009-01-29
Are you trying to create a "live" (bootable) ubuntu USB, or create a bootable USB of OS X?

---

### Post by pxwpxw on 2009-01-30
> **Jaiibee said:**
> God, I know this has probably been asking hundreds of times before and my epic researching abilities have proven their efficiency, but how exactly do I make my 4GB imation USB bootable using my Mac OS X 10.4 PPC?

I do NOT want to boot from my Mac (which is what i mostly get on gooogle), I want to make a flash drive bootable so I can actually install an OS onto my USB.

I've tried doing that disk utility and i'll try again, but please help me if you know how.

Edit: Got an "error 6, destination not configured" or something

Use the intrepid 810 installer and you should  be able to install to the whole usb drive, standard install, and if it asks, install yaboot bootloader to the usb drive.
This only works with the 810 yaboot revision (not with hardy 804 or earlier).
There is a bug with the 810 installer mounting the cdrom, there is a thread about that.

---

### Post by Jaiibee on 2009-01-30
Sorry, I didn't make my first thread more clearer..
I only have a Mac G5 PPC, which is running OS X 10.4. I have my EEE PC which I erased its operating system - completely - trying out another OS, however it didn't install properly, and now there is no OS on the EEE PC.

That's why i'm trying to install easypeasy-1.0 to my EEE PC. My EEE PC does not have a CD drive which is why I need to use my imation flash drive.

I need to get the OS onto my Imation Flash Drive, then I need to get my eee pc to boot from that flash drive so I can install it.

I'll look into yaboot etc. in a minute.
Btw, pxwpxw, are you aussy?

Edit: so yeah, I dont think Yaboot is what I need because I wont be booting EasyPeasy from an apple computer. Unless I got its purpose wrong :S Thanks though.

---

### Post by pxwpxw on 2009-01-30
> **Jaiibee said:**
> Sorry, I didn't make my first thread more clearer..
I only have a Mac G5 PPC, which is running OS X 10.4. I have my EEE PC which I erased its operating system - completely - trying out another OS, however it didn't install properly, and now there is no OS on the EEE PC.

That's why i'm trying to install easypeasy-1.0 to my EEE PC. My EEE PC does not have a CD drive which is why I need to use my imation flash drive.

I need to get the OS onto my Imation Flash Drive, then I need to get my eee pc to boot from that flash drive so I can install it.

I'll look into yaboot etc. in a minute.
Btw, pxwpxw, are you aussy?

Edit: so yeah, I dont think Yaboot is what I need because I wont be booting EasyPeasy from an apple computer. Unless I got its purpose wrong :S Thanks though.

ok, I got it wrong.

---

### Post by Jaiibee on 2009-01-30
Sorry  about that pxwpxw.
Do you know how I can configure my USB to be bootable, though?

---

### Post by pxwpxw on 2009-01-30
> **Jaiibee said:**
> Sorry  about that pxwpxw.
Do you know how I can configure my USB to be bootable, though?

If your pc can boot from usb, you should be able to find some howtos for setting up the usb with install system taken from an install CD - I think its been done for PC. Or you can probably get grub or supergrub on a usb stick and manually boot an iso file from the usb (iso of an installer CD). Once you have grub on the usb you can manually boot iso, or net install using installer images. If you had a floppy drive, a gub floppy can boot.
Thats the way I have done it, ( a long time ago).

Probably more help in the pc install forum.

---

### Post by cyberdork33 on 2009-01-30
> **pxwpxw said:**
> If your pc can boot from usb, you should be able to find some howtos for setting up the usb with install system taken from an install CD - I think its been done for PC. Or you can probably get grub or supergrub on a usb stick and manually boot an iso file from the usb (iso of an installer CD). Once you have grub on the usb you can manually boot iso, or net install using installer images. If you had a floppy drive, a gub floppy can boot.
Thats the way I have done it, ( a long time ago).

Probably more help in the pc install forum.
I think he posted here because he only has a Mac to create the bootable USB drive... but yea, you need to figure out what exactly is needed on the flash drive before anyone can help you actually do what is required.

---


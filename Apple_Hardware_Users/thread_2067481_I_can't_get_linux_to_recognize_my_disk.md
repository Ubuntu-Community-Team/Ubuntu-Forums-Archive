---
title: "I can't get linux to recognize my disk"
date: 2012-10-06
forum: Apple Hardware Users
---

### Post by eamu on 2012-10-06
Hey all!


I have had this problem since i first got my Mac Book Pro (7,1) a few years back. I've tried every Ubuntu version from 8.04 to 12.10 without any luck....


It boils down to Nvidia MCP89 and linux not being able to recognize my hd. I'm running Mac OS and Win 7 with no problems at all. I use rEFIt as boot manager.


One recent errormsg when I boot:

init: line 7 can't open dev/sda/



I've tried following [this]("https://help.ubuntu.com/community/UEFIBooting#Introduction") guide to install grub2-efi to see if that helped, but as I can't boot from anything writable like a flash drive or external hd I'm helpless.



Can anyone please guide me in the right direction?

---

### Post by albandy on 2012-10-07
Perhaps using wubi under your windows 7 installation will work.

---

### Post by eamu on 2012-10-07
> **albandy said:**
> Perhaps using wubi under your windows 7 installation will work.

I've tried that with no luck!


Today I finally got it to recognize my disk by using the ubuntu secure remix 64-bit. It booted fine and I got a message saying that EFI was detected. 

But..., what I really want is to get Backtrack running. I tried using unetbootin to make a bootable disk from the secure remix disk and then manually replacing the everything but grub. That did not work.


Is there a way to integrate grub2-efi with backtrack?

---

### Post by albandy on 2012-10-08
> **eamu said:**
> I've tried that with no luck!


Today I finally got it to recognize my disk by using the ubuntu secure remix 64-bit. It booted fine and I got a message saying that EFI was detected. 

But..., what I really want is to get Backtrack running. I tried using unetbootin to make a bootable disk from the secure remix disk and then manually replacing the everything but grub. That did not work.


Is there a way to integrate grub2-efi with backtrack?

You can run backtrack applications under ubuntu making a chroot environment or installing the same applications in ubuntu.

---

### Post by eamu on 2012-10-08
> **albandy said:**
> You can run backtrack applications under ubuntu making a chroot environment or installing the same applications in ubuntu.



Just, add the sources that backtrack use and apt-get all packages?

---


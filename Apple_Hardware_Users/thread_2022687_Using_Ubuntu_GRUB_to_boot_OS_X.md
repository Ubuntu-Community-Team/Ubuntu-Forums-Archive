---
title: "Using Ubuntu GRUB to boot OS X"
date: 2012-07-11
forum: Apple Hardware Users
---

### Post by yentl on 2012-07-11
Hello! I have  recently set up a triple boot system on a MacBook Pro 6,2 with OS X Snow  Leopard 62-bit, Windows 7 32-bit, and Ubuntu 12.04 64 bit. Currently I  am using rEFIt to boot them via a single menu but I was wondering  whether I could do the same with the GRUB installation that came with  Ubuntu. This was able to detect all three OS's, and booted into Windows  and Ubuntu fine. However when I tried to boot OS X it eventually got  stuck with the message 'Still waiting for root device'. I tried to use  this in the grub shell:

search --file --no-floppy --set=root /usr/standalone/i386/boot.efi
chainloader (${root})/usr/standalone/i386/boot.efi

But got the error 'Invalid Signature'.

I suspect it is because OS X needs to be booted with grub-efi, not  grub-pc, which is what is installed on Ubuntu. Is there a way in which I  could use the Ubuntu grub to "chainload" a grub-efi installed in the OS  X partition? I have compiled grub-efi, it was able to boot OS X without  a problem but not anything else (graphics problem with Ubuntu, maybe a  64-bit/32-bit clash with Windows?). If not, is it possible to boot into  OS X using the Ubuntu GRUB? 

Thank you!

---

### Post by tumutanzi.com on 2012-07-11
I have never tried OS X, so it sounds very strange~~~~`

---

### Post by yentl on 2012-07-27
BUMP! Sorry to bump my own thread, just hoping for some genius out there :)

---


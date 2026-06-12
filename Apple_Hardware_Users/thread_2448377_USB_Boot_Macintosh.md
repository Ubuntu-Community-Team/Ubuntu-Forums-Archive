---
title: "USB Boot Macintosh"
date: 2020-08-06
forum: Apple Hardware Users
---

### Post by alanglenn74 on 2020-08-06
I have a couple year old MacBook Pro.

I USB booted it and split the hard drive to install a dual boot. Then I installed Ubuntu 20.04 LTS while looking for the dual boot option but never saw it. I don't think it was there. I continued to install with the assumption I'd boot from USB to fix it. Before, I would USB boot off the EFI application at the beginning that showed at boot. It looks like Ubuntu overwrote that. Now, it goes straight into Ubuntu.

I'm thinking since it has been replaced with Ubuntu software, it knows what to do about it. But, I don't know how to tell it. Also, this is a BIOSless machine, there is a way to set the BIOSish things by the OS or at the Grub level. I'd love to figure out how to dual boot. I'd rather leave a setting that it boots from USB if it can always.

I'd like to tell Grub to dual boot. I fear doing it by just messing with the boot info when the machine is booted because if I screw up, I have a brick.

Currently, I'm only using half my hard drive and I will never be able to switch OSs. Not being able to switch OSs is somewhat bad because MacBook Pros can have long lifetimes.

---

### Post by wildmanne39 on 2020-08-06
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by alanrichardbarker on 2020-08-07
You could try installing rEFInd boot loader.

[https://www.rodsbooks.com/refind/index.html](https://www.rodsbooks.com/refind/index.html)

---

### Post by gsahli on 2020-08-07
Two things to try:
in the linux terminal, run the command sudo update-grub
The install should have done this, but it won't hurt to try again.
Or, reboot and immediately press and hold the "Option" key, until the Mac Boot selector shows boot options.
(Grub is a boot manager, the Option key is a boot manager, and rEFInd is a boot manager. Each can give you dual boot capability)

---

### Post by alanglenn74 on 2020-08-07
Thanks for the info guys. I had tried the option key, as that was the key you'd use with the original Mac boot manager. It didn't work for me.

But, rEFInd worked great! Thanks guys!

---


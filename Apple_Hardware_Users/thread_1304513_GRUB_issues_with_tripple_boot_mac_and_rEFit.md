---
title: "GRUB issues with tripple boot mac and rEFit"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by TopCat33 on 2009-10-29
Edit: NVM, can a Mod delete this. I got it to work. As it turns out I never told Grub to install on SDA4, I kept trying to install it and it kept trying to put it on SDA, which my Macbook's EFI wouldn't allow, and so it eventually just shoved it on SDA3, which actually turned out to be my Windows Partition.

I have since run 7's equivalent of FIXMBR, and got it's boot loader back, as well as reinstalled Ubuntu on it's specified partition, and then at the end clicked advanced and switched the boot loader location from SDA, to SDA4. Now it works fine

---


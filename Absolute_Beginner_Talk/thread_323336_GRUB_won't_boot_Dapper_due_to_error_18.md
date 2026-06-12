---
title: "GRUB won't boot Dapper due to error 18"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by rey1321 on 2006-12-21
Hi guys! I new w/ubuntu I installed Dapper to 2 weeks ago, and everything work fine, But now that I want to boot it hangs at the GRUB screen with this:

GRUB Loading, Please wait- (and then after a minute or so of waiting another message)
Error 18                             (and then I got tired of waiting and noting happened)



PLEASEEE  HEEEEELP ME!!!!!!!!!!!!

---

### Post by Ferri on 2006-12-22
Apparently your hard disk is bigger than your BIOS can handle. You can get some information here:
[COLOR="Blue"][http://wiki.linuxquestions.org/wiki/GRUB]("GRUB wiki")[/COLOR]
It's supposed to be solved if you create a boot partition completely within the first 1023 cylinders of your hard disk.

---


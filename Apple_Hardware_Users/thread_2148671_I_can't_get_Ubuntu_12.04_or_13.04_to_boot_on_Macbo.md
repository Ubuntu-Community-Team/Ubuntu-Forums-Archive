---
title: "I can't get Ubuntu 12.04 or 13.04 to boot on Macbook Pro 9,2"
date: 2013-05-26
forum: Apple Hardware Users
---

### Post by skamsie on 2013-05-26
Hello everyone,

I have been trying for the last 3 days to get ubuntu to work on my notebook, a macbook pro 9,2 (with ssd if that makes any difference). I have no problem with the installation as I made it install from USB stick or directly from the Live CD, both 12.04 and 13.04. The problem is, that after the install, when I try to boot into ubuntu using the refit menu, after i select the Linux partition to boot from, I only get the penguin logo and after that just a black screen (sometimes with a blinking cursor, sometimes not). I have followed several threads on this blinking cursor problem and they all imply some fixes in the grub menu, but i do not see any menu, just the black screen immediately after the logo.

For installing i have used this: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
Of course i have also followed different installation methods found on other sites, but i always got the same result. 

If there is already a fix for that, please point me in the right direction and i apologize for opening new thread. If not, maybe someone can help.

Thanks!

---

### Post by sanderj on 2013-05-26
In the first second of the GRUB boot, can you press F6 (does a Mac have Function keys?)?

If so: remove the boot options "splash quiet", press Enter, and see what happens.

---

### Post by skamsie on 2013-05-26
> **sanderj said:**
> In the first second of the GRUB boot, can you press F6 (does a Mac have Function keys?)?

If so: remove the boot options "splash quiet", press Enter, and see what happens.

Yes it has functional keys, but i do not get the GRUB boot. That is the problem...

---

### Post by sanderj on 2013-05-26
start pressing F6 ...

---

### Post by skamsie on 2013-05-26
It doesn't work. I get the same result. I guess the problem is GRUB does not install

---


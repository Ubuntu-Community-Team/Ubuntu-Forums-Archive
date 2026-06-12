---
title: "Booting from USB"
date: 2011-05-18
forum: Apple Hardware Users
---

### Post by 3dmaker on 2011-05-18
Hey guys, ok so I have searched for days, and tried many things to make this work.

I am trying to create a bootable Ubuntu live USB that can load from a Mac. I have rEFIt installed on my mac.

I have gotten as far as getting into the grub, and loading the kernel, but there is always some sort of panic. I have searched for many guides, and a lot of them are dated. Is there any simple step by step information that can help me get this to work.

Edit:
I would use this site:
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

but its down!

---

### Post by paulionvc on 2011-05-18
I'm looking to do the same thing.

---

### Post by 3dmaker on 2011-05-19
I have complied the latest grub 1.99 by following directions on here:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I have rEFIt installed, and it sees the my grub, it loads a menu, but when it starts loading files, it stops. I need to know a way to custom create a grub.efi file, because the way I have done it many commands dont work. For example it says "error: unknown command `root`"

---

### Post by siepo on 2011-05-19
I got lucky with the recipe from this page:

[http://www.devslashzero.com/node/160](http://www.devslashzero.com/node/160)

For me, it worked fine with Natty.

---

### Post by 3dmaker on 2011-05-19
It doesn't work for me, I have the MacBookPro6,2

---


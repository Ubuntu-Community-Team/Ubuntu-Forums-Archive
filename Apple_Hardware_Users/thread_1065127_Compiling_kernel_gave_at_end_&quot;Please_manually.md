---
title: "Compiling kernel gave at end: &quot;Please manually create an initrd image&quot;"
date: 2009-02-09
forum: Apple Hardware Users
---

### Post by tarekeldeeb on 2009-02-09
Hello all,

I have ubuntu 8.10 on AMD64, and an unsupported dvb-s card, and a patch for the card against 2.6.27.10.

I downloaded the kernel >> applied patch >> configure >> compile.
I followed the official documentation [here]("https://help.ubuntu.com/community/Kernel/Compile")

finally, the deb packages are created ..

* linux-xenu-2.6.27.10_2.6.27.10-10.00.Custom_amd64.deb
* linux-headers-2.6.27.10_2.6.27.10-10.00.Custom_amd64.deb

 I installed the "linux-xenu".. succeeded but it gave me:
"Please manually create an initrd image"

then I installed the "linux-headers" .. successfully.


Nothing was changed in my grub menulst, and of course , no initrd was created.

I googled but knew that I need: mkinitrd, which is not found through apt-get ..

Does any1 have a clue?

Thanks in advance,
Tarek

---

### Post by tarekeldeeb on 2009-02-09
sorry .. i duplicated this thread ..
pls remove this thread!

---


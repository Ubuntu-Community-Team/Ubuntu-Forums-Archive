---
title: "Need to extract boot image from CD and burn a new CD with it"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2007-06-09
I have been trying to edit a bootable CD, for which I have to extract the boot image and boot catalog, change the file content, and put it all back. On Windows I used to do it in ISObuster and CDburnerXP or some other programs which let me do all this. However, I can't find any suitable software in Ubuntu for it, or just can't find the way to do it. First, I found that it was possible to extract the boot image/catalog with dd but I am not sure I did it right. Then, I was surprised that gnomebaker did not support making bootable CDs, so I suppose mkisofs can do it, though I don't know how. Please recommend something, hopefully someone has already been in such a situation.

---

### Post by p_quarles on 2007-06-09
According to my guide (Ubuntu Hacks, O'Reilly 2006), you need the following:

-cloop-utils
-mkisofs
-squashfs-tools

---

### Post by NT4.0 on 2007-06-09
I downloaded the tools but I guess I need to learn more. I tried to feed the extract_compressed_fs the ISO image but with no result. As far as I know, the other two (create_* and mksquashfs) are used to create boot images or CDs but not to extract.

---

### Post by p_quarles on 2007-06-09
You don't need any extra tools to extract and mount a read/write version of the filesystem. Here are a couple of tutorials; both basically match what I read in my reference book:

[http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html](http://blogs.adobe.com/penguin.swf/2006/09/customizing_ubuntu_live_cd_606_1.html)

[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

---

### Post by NT4.0 on 2007-06-10
Thanks! Now I not only know how to manage mkisofs to make bootatble CDs but also how to work with squashfs (I noticed this file on the Ubuntu CD but didn't know how to unpack it before).

One issue that remains unclear: I didn't know that the boot image and boot catalog were already on the Ubuntu CD in another folder. What if I need to extract the boot image from any bootable CD?

---


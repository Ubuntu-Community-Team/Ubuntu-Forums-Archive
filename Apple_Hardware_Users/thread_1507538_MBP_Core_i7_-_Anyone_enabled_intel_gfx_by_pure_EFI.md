---
title: "MBP Core i7 - Anyone enabled intel gfx by pure EFI boot(grub2)?"
date: 2010-06-11
forum: Apple Hardware Users
---

### Post by dmhummel on 2010-06-11
After working with my new Macbook pro (core i7 17 inch), I have successfully installed Ubuntu 10.04 with sound and all that stuff.  However, I really care about battery life so my last issue is to enable the integrated graphics.  From my detective work I assume the following.  Please let me know if anything I have here is wrong -

1) Intel graphics are hidden by apples Bios emulation and may only be accessed by booting in pure EFI. 
2) Booting in pure EFI is possible by booting Ubuntu via a EFI GRUB2 configuration.

Before I spend too much time trying #2,  I'd like to know if anyone has done.  When it was done, could you see the intel video card.  Could you use it?

Thanks~

---

### Post by dmhummel on 2010-06-15
No one is booting a 2010 MBP via EFI enabled grub?

---

### Post by Taoye on 2010-08-22
I've tried, and failed.

Mine is the Macbook Pro 5,5 with nVidia 9400m. Using grub-efi I can boot into Fedora 13 in pure EFI mode, and I can get compositing graphics if I use the nonfree nvidia driver, but I tried a similar setup with Ubuntu and it won't even boot. For some reason grub freezes when it tries to boot the ubuntu kernel. Can't figure out why.

---

### Post by Sidolin on 2010-08-22
I tried it and didn't get it to work yet. Efi boot worked after some fiddling around but it still uses the nvidia card by default and switcheroo doesn't seem to detect anything.

---

### Post by metatechbe on 2010-08-22
> **dmhummel said:**
> 
2) Booting in pure EFI is possible by booting Ubuntu via a EFI GRUB2 configuration.


dmhummel,

Your kernel has to be compiled with the address of the video framebuffer of your integrated graphics.
Please see the thread [http://ubuntuforums.org/showthread.php?t=1557326](http://ubuntuforums.org/showthread.php?t=1557326) and reply with the output of the command in the post.
[Edit : wrong answer, please check here: [http://grub.enbug.org/TestingOnMacbook]](http://grub.enbug.org/TestingOnMacbook])

Thanks,

metatech

---


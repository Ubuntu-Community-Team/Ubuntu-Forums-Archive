---
title: "How exactly does a dual-boot work?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by GrahamCracker on 2007-05-06
If I installed Ubuntu on a computer that already has Windows XP (but is slow), how would I switch between one OS and the other?  On another forum, a reply was: 

"Just do a dual boot install. Grub will ask each time when you 
start the computer which OS you want to run."

Now I've installed a couple of OSs before (Win98SE and Win 2000) and I know how to change BIOS settings, etc., but I'm not sure what this means.  I've never heard of "Grub" before.  Can I just do an Ubuntu doiwnload and follow the prompts, or is it more complicated?  Is there an option for which OS is the default, or will there be a prompt when I turn the computer on, asking me which OS I want to run?  I am asking this because I don't want to screw up my existing OS, which is slow but works.

Thanks.

---

### Post by aysiu on 2007-05-06
Grub is Ubuntu's bootloader program that installs to the Master Boot Record of your computer (also known as the MBR). The Grub bootloader usually automatically adds Windows to the boot menu, so you'll get a little menu that lists Ubuntu and Windows when you boot up. Then, you just press the up and down arrows to select which OS you want to boot into.

More details here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---


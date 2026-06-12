---
title: "Need help w/boot sequence"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by JGKC9AYC on 2006-05-13
It seems that after the timeout my pc automatically boots into Ubuntu instead of XP.
How can I edit my grub menu for XP to boot by default instead of Ubuntu.
Also, in my grub menu, there's 4 instances of Ubuntu:

[I]title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot
[/I]
Do I need to see (what I assume is) the older kernels?  If not, do I just add the "#" beside them?

Thanks in advance!

---

### Post by kencoe on 2006-05-16
Here is a link to an article on this subject. You can also look at the menu.1st file inside the grub directory. It has instructions on changing the default boot somewhere around line 6. 

[http://www.linuxforums.org/forum/linux-newbie/7324-how-do-i-change-boot-order-grub.html](http://www.linuxforums.org/forum/linux-newbie/7324-how-do-i-change-boot-order-grub.html)

You can comment out those extra boot options, but it will cause a problem if you ever have to back up to the last kernal for troubleshooting. Most people leave the last ones in...

---

### Post by aysiu on 2006-05-16
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by kencoe on 2006-05-16
[QUOTE=aysiu][https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)[/QUOTE]

Thanks for the updated link. I must have missed that one to give him. Your link has much easier directions than mine. 

Follow this one. It's easier to understand.

---


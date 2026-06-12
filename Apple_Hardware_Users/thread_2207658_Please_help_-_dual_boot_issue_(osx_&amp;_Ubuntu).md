---
title: "Please help - dual boot issue (osx &amp; Ubuntu)"
date: 2014-02-24
forum: Apple Hardware Users
---

### Post by Smincho on 2014-02-24
Hello 

just wondering if someone might be able to help with my issue. I wanted to dual boot my mac so it had both OSX and Ubuntu. I followed instructions on how to do this partitioning my hard drive and installing refit so I could choose between the two systems. I installed Ubuntu to the partition but when I rebooted to access OSX the refit options had gone and instead I was left with an error message and the GRUB choice screen (see picture attachments). From this menu I can load up Ubuntu fine, but mac osx won't load (32 bit - error: kernal doesn't contain suitable 32 bit architecture; 64-bit - screen just goes blank and osx never loads).

Has anyone had this error before, not sure what to do :s

Thanks 

Sminch

---

### Post by QIII on 2014-02-24
*Moved to **Apple Users***

---

### Post by zircon_34 on 2014-02-24
I would try to reboot holding the option key, or option and R, and go into OSX, reinstall refit and try to reboot several times (sometimes refit doesn't show up the first time). While you are at it, I would install refind instead of refit, as refit is outdated and no longer maintained.

I read somewhere that there is a way to boot OSX in the Grub2 menu (your situation), but you need to modify a configuration file in Ubuntu (using a text editor), can't recall the exact command...anyone knows more about this?

---

### Post by Smincho on 2014-02-25
Thanks Zircon, however whenever I boot with 'option ' or 'option + R' it still takes me into the GRUB screen where I cannot boot OSX from. Getting a bit worried now as I need OSX for work :s I seem to have my OSX files on Ubuntu but obviously can't use them. If I booted from my snow leopard installation cd would I lose all my files on my OSX partitioned drive?

---

### Post by zircon_34 on 2014-02-25
no you shouldnt loose your files unless you install OSX again. I also saved my mac once like that. As I recall you should get an option to boot into your system either directly or after you boot in repair mode.hope that helps. its difficult to see the problem cause I do not know which method you used for the ubuntu install and how you partitioned your system. There is a partition called EFI and then your OSX partition that you should not delete. then your system should be safe

---

### Post by Smincho on 2014-02-25
Hi Zircon,

I managed to fix the problem by using my snow leopard installation cd to boot into OSX and then used my OSX partitioned hard drive as a startup disk which gave me access to my old files. I then deleted refit and installed refind instead. When I booted back up I now get the refind menu which works perfectly so I can select between the two operating systems :D

Thanks for your help!

Sminch

---

### Post by zircon_34 on 2014-02-25
Great:D enjoy your dual boot!

---


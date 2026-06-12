---
title: "Dual booting?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by klain on 2007-12-17
Ok heres the deal, 

i'm a complete beginer with ubuntu and linux everything confuses me and and treating me like a complete idiot is advised

Now for some unknown reason i bought vista (64-bit) and wishing to expand my knowledge of computers i thought it would be a good idea to install ubuntu (64-bit).

So the plan is to duel boot between vista and ubuntu.

I already have vista installed, I partitioned it so i had over 100 gb left (500gb Hard drive).

I have tried a guide before but it installed ubuntu and messed up my vista boot loader, it then continued to boot saying missing operating system

Now if anyone can help me with a step by step guide (that works for ubuntu 7.10) to dual booting i would be most thankful.

---

### Post by logos34 on 2007-12-17
try these guides:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

or using vista boot manager to load linux instead of grub:

[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by rbc on 2007-12-17
Try this. It's written for 7.04, but the installation should be the same for 7.10
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by klain on 2007-12-17
thanks guys will let you know how i get on!

---

### Post by Ub1476 on 2007-12-17
Is there any specific reason for running 64 bit?

It's not really necessary to run it, unless you're going to do some heavy virtualising/photoshop, cd ripping work.

Since you're a first time Linux user I recommend you the standard 32 bit. It will give a much more pleasant experience.

---

### Post by klain on 2007-12-19
Hi Guys,

Thanks for every ones advice, this is the best thing about open source everyone helping each other.

Anyway, I followed the guide here for ubuntu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu#](http://neosmart.net/wiki/display/EBCD/Ubuntu#)

Everything went fine and i managed to get into vista to use EasyBCD.

I then rebooted and selected ubuntu from the boot list, it booted partially then paused, heres a snipet of what I saw:

Turning on gate A20....Success
Starting CMain()...Find --Set-Root          --ignore-floppies /boot/grub/menu.Lst

And thats it,

Again many thanks for everyones input

---

### Post by klain on 2007-12-20
> **Ub1476 said:**
> Is there any specific reason for running 64 bit?

It's not really necessary to run it, unless you're going to do some heavy virtualising/photoshop, cd ripping work.

Since you're a first time Linux user I recommend you the standard 32 bit. It will give a much more pleasant experience.

I hope to use photoshop eventually and film editing things for visual effects

EDIT: And possibly modeling

---

### Post by klain on 2007-12-22
> **klain said:**
> I hope to use photoshop eventually and film editing things for visual effects

EDIT: And possibly modeling

If i used the 32 bit version would i still have this issue?

---

### Post by seventhc on 2007-12-22
I'm not sure if it's the same for 64 bit or not. But on the 32 bit if you already have vista installed and a free partition then during the install of ubuntu you can choose  to let ubuntu use the free remaining space guided. It will partition the remaining space for you and set up your boot menu. No need for EasyBCD

---


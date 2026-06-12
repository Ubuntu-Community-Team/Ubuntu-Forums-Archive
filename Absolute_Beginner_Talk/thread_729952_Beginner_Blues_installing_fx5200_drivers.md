---
title: "Beginner Blues installing fx5200 drivers"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by mart-leeds on 2008-03-20
Hi

I know theres a million different threads reagrding this but, as iam a complete newcomer to ubuntu i wondered if any body could give me a little guidance installing a nvidia fx5200 driver in an easy to follow guide.

I have recently installed ubuntu after benn a faithful windows user for 10 years, i have sucesfuly installed ubuntu, which i must admit was a breath of fresh air after spending 40 minutes guiding winxp thriugh its install.

my question is how do i install the nvidia drivers, i downloaded a driver from the nvidia website onto a usb memory stick   how do i then install it using ubuntu.
I know theres a solution to this elsewhere on the forum but im struggling somewhat trying to understand what to do.

Thanks in advance

---

### Post by bumanie on 2008-03-20
Before you install that go to System --> Administration --> Restricted drivers. Enable your card that way. It should work OK. If you install the one from nvidia, you will have problems when there is a kernel upgrade. One really only needs to install the nvidia .run if Resticted drivers doesn't work.

---

### Post by mart-leeds on 2008-03-20
Hi

Thjat was the first thing i did, unfortunatly i recieved a message stating it was not a supported card, or a supported driver then and refused to enable the card.

---

### Post by bumanie on 2008-03-20
I guess you'll have to use the altrnative method, which as I said can cause problems with kernel updates.

[http://www.nvidia.com/object/linux_d...32_169.12.html](http://www.nvidia.com/object/linux_d...32_169.12.html) Please transfer the file you have on your usb to desktop or download a new one to the desktop from the above site and follow these instructions.

Stop xserver ctrl-alt-F1 together
enter username and password
> sudo /etc/init.d/gdm stop   --> hit enter
> sudo cd ~/Desktop  [/QUOTE --> hit enter
[QUOTE]sh NVIDIA-Linux-x86-169.12.pkg1.run   --> hit enter 
> sudo /etc/init.d/gdm start   --> hit enter
If gui doesn't start either sudo reboot or try ctrl-alt-F7
Hope this works for you. It did for me.

---

### Post by louieb on 2008-03-20
I have 2 AGP nvidia  FX5200 (EVGA brand) installed in different computers.  Both the stock NV driver and the restricted nvidia driver work out of the box. 

Just wondering if you have the PCI version of that card? Have seen a few posts about the PCI FX5200  installed on a PC that has on-board graphics also. Unfortunately have seen a fix for that yet. Let us know if bumanie's fix works. Good luck.

---


---
title: "Ubuntu AMD64"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by discoian on 2006-08-25
Hi there,

I have an AMD64 therefore I thought it would be right to install Ubuntu for AMD64.  However, I cannot install the Flashplayer as it states it does not work for my cpu architecture.

Any ideas?

When I installed Ubuntu, it set up a dual boot with my WinXP installation.  As I am now thinking of installing the i386 version of Ubuntu, will that kill the bootloader or just re-configure it and work as before?

And finally...Ubuntu or Kubuntu?  I have always been a fan previously of KDE and hated Gnome, but I am not so sure now.  Gnome appears to be better but KDE is more familiar to those who have been brainwashed into running Windows all their lives.

---

### Post by amo-ej1 on 2006-08-25
It's easy to understand, the flashplayer is a binary release that was compiled for a 32bit architectur and will not work out of the box on a amd64 machine. afaik there is no 64 bit binary flashplayer that gets distributed.The only solution is to get a 32 bit environment set up with a 32 bit firefox, this is described at the following location: [http://http://ubuntuforums.org/showthread.php?t=24575]("http://http://ubuntuforums.org/showthread.php?t=24575")

and kde/gnome is simply a choice of personal taste

---

### Post by x64Jimbo on 2006-08-25
*Obligatory remark about running the Windows version of Firefox through Wine to achieve even better results*

---

### Post by discoian on 2006-08-25
Ok, but if I overinstall the i386 version of ubuntu/kubuntu, will this cock up the bootloader?

---

### Post by harisund on 2006-08-25
Are you planning to overwrite the AMD64 partition with i386? If so, the grub will be overwritten appropriately. It will just show the i386 kernels and the Windows partition.

---

### Post by discoian on 2006-08-25
Yes I will be overwriting with the i386 version.

---

### Post by harisund on 2006-08-25
Then typically you wouldn't be facing any problem. 

If it is possible, can you tell me how your hard disk is partitioned and what partition has what currently on it? This way I will be able to give you a complete explanation of what is going on, so that you will be in a better position to debug if necessary.

---


---
title: "Dual booting Fedora 16 and Ubuntu 10.04 LTS"
date: 2011-11-13
forum: Any Other OS
---

### Post by tech291083 on 2011-11-13
Hi,

I am thinking of dual-booting 

1. Fedora 16 (the latest) and Ubuntu 10.04 LTS (support until 2013-04)

or

2. Fedora 16 and Ubuntu 11.10 (support until 2013-04)

Which of the 2 above I should go for? Thanks.

---

### Post by tech291083 on 2011-11-14
Please help me guys, thanks.

---

### Post by Uchiha_Kori on 2011-11-14
Pesonally, and this is just my opinion, you should dual boot Fedora 16 and Ubuntu 11.04 LTS. 

Again, this is just my personal preference. Your getting the best of both if you dual boot both. I do not suggest installing Ubuntu 11.10 just because it is focused on Unity, however, Unity may be something you like. I just don't like Ubuntu 11.10.

---

### Post by snowpine on 2011-11-14
My personal opinion is to choose one distro and stick with it. You haven't explained your reasons for needing/wanting a dual boot.

Then the only question becomes: Ubuntu or Fedora? and I'm not going to open that can of worms. ;)

---

### Post by howefield on 2011-11-14
There is no right and wrong here, so all you'll get is opinions.

Mine is if you have a reason for installing multiple boots, then you can triple boot just as easily as dual. :-)

What are you currently using ?

---

### Post by Uchiha_Kori on 2011-11-14
> **snowpine said:**
> My personal opinion is to choose one distro and stick with it. You haven't explained your reasons for needing/wanting a dual boot.

Then the only question becomes: Ubuntu or Fedora? and I'm not going to open that can of worms. ;)

Well said.

---

### Post by tech291083 on 2011-11-14
> **Uchiha_Kori said:**
> Pesonally, and this is just my opinion, you should dual boot Fedora 16 and Ubuntu 11.04 LTS. 

Again, this is just my personal preference. Your getting the best of both if you dual boot both. I do not suggest installing Ubuntu 11.10 just because it is focused on Unity, however, Unity may be something you like. I just don't like Ubuntu 11.10.


Hi,

Yes, its ok if you recommend Ubuntu 11.04 LTS as it has long term support and its also makes sense to me. Actually I have been triple booting Windows XP, Fedora 14 and Ubuntu 10.10 for the last 4/5 months although I had to make a few settings as initially it simply did not work at all, but I was adamant to make it happen and eventually it did. I love both Fedora and Ubuntu equally and they both are fine with me. So I would love to continue my personal habit of dual-booting them both if not triple-booting with Windows. I want to learn things, that is all. 

I have just downloaded and install the latest Fedora 16. But by default it has Gnome as desktop environment and I like KDE more. I today tried to find this file in Fedora 16 called /boot/grub/menu.lst but I simple could not find it not was I able to locate /etc/grub.cong as you know these two are very crucial files if one wants to set the boot menu timings and add or remove other OS to Fedora. So I am worried as to how I am going to cope with the default KDE environment. I think I can install install KDE as well and use it at login time. I also hope that this will also me a new environment where I will able able to access these 2 file without much problem and eventually able to dual boot with Ubuntu, so this is the short story. Please do reply with your suggestions if any, thanks a lot to all of you who have replied so far.

Please note that I do not intend to criticize Gnome here, it is just that I am not that familiar with it. Thanks.

---

### Post by howefield on 2011-11-14
> **tech291083 said:**
> I today tried to find this file in Fedora 16 called /boot/grub/menu.lst but I simple could not find it not was I able to locate /etc/grub.cong as you know these two are very crucial files if one wants to set the boot menu timings and add or remove other OS to Fedora.

Fedora 16 has Grub2, so you won't find those files. Fedora should  be easier to multiple boot with than previous versions.

---

### Post by tech291083 on 2011-11-14
I just hope that installing KDE will make it easier for me to edit those 2 files required for dual/multi booting other OS with Fedora 16, thanks.

---

### Post by snowpine on 2011-11-14
> **tech291083 said:**
> I just hope that installing KDE will make it easier for me to edit those 2 files required for dual/multi booting other OS with Fedora 16, thanks.

Your choice of KDE vs. Gnome is irrelevant to GRUB.

Fedora and Ubuntu both now use Grub 2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://fedoraproject.org/wiki/Grub2](http://fedoraproject.org/wiki/Grub2)

If you already have a working dual boot of Fedora and Ubuntu, then you just need to upgrade, you don't need to reinstall. :)

---

### Post by tech291083 on 2011-11-15
> **howefield said:**
> Fedora 16 has Grub2, so you won't find those files. Fedora should  be easier to multiple boot with than previous versions.


Ok. so Grub 2 is the reason. But how do I edit boot menu and set boot time etc?

> **howefield said:**
> 
Fedora should  be easier to multiple boot with than previous  versions.


You mean the latest Fedora 16? If so, then I am really glad to hear that. Thanks a lot.

---

### Post by mips on 2011-11-15
> **tech291083 said:**
> Ok. so Grub 2 is the reason. But he how do I edit boot menu and boot time etc?


You don't need to edit the menu, if you reinstall grub with a new distro it will automatically pick up existing distros and add them. If you don't reisntall grub you can run a command to update the menu. If you want to edit the time etc look at /etc/default/grub.

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId16468](http://www.dedoimedo.com/computers/grub-2.html#mozTocId16468)
[https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior](https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior)
[https://wiki.archlinux.org/index.php/GRUB2#grub-mkconfig](https://wiki.archlinux.org/index.php/GRUB2#grub-mkconfig)

---

### Post by fantab on 2011-11-15
I dual boot Ubuntu Oneiric with Fedora Verne, my favorite Linux Distros. I cannot choose between them, so i have 'em both. :cool: 
Because of Grub-Legacy in previous versions of Fedora I used Ubuntu-Grub2. I am glad though that Fedora is now shipped with Grub2. 

Suggestion to OP... Use Grub2 from Ubuntu as it is easier to work with in Ubuntu. When you install Fedora just choose NOT TO install GRUB  and after installation log into Ubuntu and 

$sudo update-grub

Fedora will be waiting for you next time you see grub menu.

---

### Post by tech291083 on 2011-11-21
> **fantab said:**
> 
Suggestion to OP... Use Grub2 from Ubuntu as it is easier to work with in Ubuntu. When you install Fedora just choose NOT TO install GRUB  and after installation log into Ubuntu and 

$sudo update-grub

Fedora will be waiting for you next time you see grub menu.

Ok, my plan is to install Fedora 16 and then Ubuntu 10.04 LTS. So as per your suggestion I should not install Fedora Grub and only install Ubuntu Grub? This is realy interesting. I will give this a try and see how it goes. thanks.

---


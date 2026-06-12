---
title: "Ubuntu 7.04 beta installation destroyed my vista."
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by xoxs on 2007-04-10
I have a very serious problem. I basically installed Ubuntu 7.04 on my Creative Zen Vision:M which i have partitioned so that it's a removable hard disc. After installing it though i have noticed that it will not boot my vista, not even looking at that menu with booting options. It's as if it has told my computer that vista doesn't exist. I have checked the boot and made it boot from my main hard disc, but it seems that Linux has overridden that and made it impossible for me to boot from Windows as standard.

So in conclusion it has destroyed everything. Because i can't re-install vista, i used the upgrade version, which means that you have to have a version of Windows on you're computer to use the license. So basically Ubuntu has destroyed everything for me. Anyone who can help me?

---

### Post by chakkaradeep on 2007-04-10
> **xoxs said:**
> 
So in conclusion it has destroyed everything. Because i can't re-install vista, i used the upgrade version, which means that you have to have a version of Windows on you're computer to use the license. So basically Ubuntu has destroyed everything for me. Anyone who can help me?

If you can boot into ubuntu, please do the following,

1) open the Terminal *Applications->Accessories->Terminal*

2) Type, *sudo fdisk -l* (it will prompt for password, type your password)

3) Paste the contents here

If am correct you installed Ubuntu in a external hard disk ?

---

### Post by nudnik on 2007-04-10
> **xoxs said:**
> I have a very serious problem. I basically installed Ubuntu 7.04 on my Creative Zen Vision:M which i have partitioned so that it's a removable hard disc. After installing it though i have noticed that it will not boot my vista, not even looking at that menu with booting options. It's as if it has told my computer that vista doesn't exist. I have checked the boot and made it boot from my main hard disc, but it seems that Linux has overridden that and made it impossible for me to boot from Windows as standard.

So in conclusion it has destroyed everything. Because i can't re-install vista, i used the upgrade version, which means that you have to have a version of Windows on you're computer to use the license. So basically Ubuntu has destroyed everything for me. Anyone who can help me?

If you have a Vista install disk, you can set the BIOS to boot from that (if needed) and choose the repair option from the menu. When that window appears, you can select the "Command Prompt" option, instruct DOS to go to whatever drive Vista is installed on. If that happens to be C for example, you would type "c:". If it successfully makes it to the Vista drive, type the following "bootrec/fixmbr" That will restore the Vista bootloader, and will almost certainly make it impossible to boot Ubuntu. Vista costs about 200 dollars US, however, and since there are no licensing worries with Ubuntu, if you have to loose something, or reinstall, Ubuntu is the painless choice. Hope this helps. 

See mascot below....

---

### Post by xoxs on 2007-04-10
thank you both. Anyways about what you said about money that wasn't a big problem. I am a student and i got a great deal of.

Thanks Again.

---


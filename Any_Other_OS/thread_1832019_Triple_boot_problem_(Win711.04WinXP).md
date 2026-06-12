---
title: "Triple boot problem (Win7/11.04/WinXP)"
date: 2011-08-24
forum: Any Other OS
---

### Post by slcooper on 2011-08-24
I'm experiencing a mild panic attack while writing this, so I hope I got it in the right subforum. My laptop originally had Windows 7 on it - and I installed Ubuntu in a dual boot. Now I had to install Windows XP due to incompatibility of some programs with Seven, and problems started.

First, I wasn't able to boot ubuntu, but editing the grub via live cd did the trick - now I have the grub loader choice between ubuntu and Windows 7 loader - which when chosen shows to be Windows XP loader!

How can I retrieve my Windows 7 loader and have real triple boot?

---

### Post by tommpogg on 2011-08-24
did you try to run the command update-grub?

---

### Post by slcooper on 2011-08-24
I have, it updates to the same condition. I have a weird feeling that Windows XP has overwritten the Windows 7's loader completely - so my question might have been - how to reinstall Windows 7's loader without removing the XP's loader, and without uninstall of either one.

If that is not possible, then what can I do to recover 7 and get rid of XP for good? I know this sounds like a question for Microsoft support, but I hoped for an answer here.

---

### Post by tommpogg on 2011-08-24
Take a look [here]("http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html"). It seems it is possible to use a tool called [EasyBCD]("http://neosmart.net/dl.php?id=1") to fix the boot loader.
Notice that I have found it on google and I have not tried it. Thus, I am not sure if it is going to work.

---

### Post by slcooper on 2011-08-24
Yep, that is it! I tried EasyBCD already, but I didn't know it required .NET framework, so it failed every time - but now it worked like a charm and I got Windows boot menu. After that I plugged in my Natty USB, restored GRUB and after restart - voila: I have a choice between Ubuntu and Windows, and choosing Windows leads to Windows boot selection menu, with XP and 7 as options. 

Thanks a lot! Case solved.

---


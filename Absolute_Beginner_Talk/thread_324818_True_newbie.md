---
title: "True newbie"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by netGerm on 2006-12-24
Hi,  I just started using this OS about two weeks ago and have been messing with it since.  I love it.  I'm hoping that this will expand my knowledge in Linux and hopefully I can start using other distros comfortably in the future.  But, I love the layout of Ubuntu and the installation was as easy as it comes.  When I installed, everything was smooth.  I didn't have to find any drivers for anything, as they were "automatically" there (video, sound, network, etc).  I finally have Beryl and Xgl working smoothly too :)

My question, I recommended my best friend to give Ubuntu a try because he curses VVindows everyday.  He boots to CD and after the loading screen, the Ubuntu square box that shows you what's loading right before it gets to desktop, is distorted and he can't see what's there.  Then it just sits there and locks up.  He tried Safe Mode, no luck.  He checked CD integrity, it's fine.  He even burned 3 different CD's using different software, no luck.  The CD works fine in my computer.  I thought it was video driver issue, but wouldn't it still boot in Safe Mode?

My computer is 4 years old with older hardware (AGP, AMD XP, etc).  He built his a few months ago and has the latest video card, AMD64, etc.  I don't understand why he can't run it on his PC.  Any suggestions would be great.

---

### Post by pseudonym on 2006-12-24
He should try booting with the 'noapic' option. The kernel on the install CD often won't work with new machines unless you use the kind of 'legacy' mode that 'noapic' gives you.

To get to the boot prompt on the installer press F6 at the first screen, then hit escape, and enter to answer 'yes' to the question which will come up. If you are unable to get to this point you may need to download the 'alternate' install CD which has more boot options.

HTH

---

### Post by netGerm on 2006-12-24
If it does work and it boots to CD, and then he installs it to HD, it should boot up properly thereafter?  I'll tell him to give your suggestion a try and see what it does.  Thanks :)

---

### Post by pseudonym on 2006-12-24
Yep, because the bootloader will be automatically configured to use 'noapic'. Once you're up and running, if you're feeling adventurous you can then try and build yourself a 2.6.19 kernel (search 'kernel compiling for newbies' in the howto section). Depending on the hardware, this should enable you to boot without 'noapic', which will give you 23 IRQs instead of the standard 15. But the system should still work fine with the default kernel.

---


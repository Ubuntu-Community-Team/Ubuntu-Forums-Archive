---
title: "Dual Boot Vista/Ubuntu Bootloader Problem"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by mmm_unit on 2008-02-02
So I installed Vista then Linux and I did not want to use the linux GRUB, so I installed EasyBCD bootloader to help with my dual booting needs.  I used EasyBCD to replace the Linux GRUB with Vista's bootloader (or that's what it should have done) and I configured EasyBCD to have a Linux input, but when I boot up, it skips right through the dual boot options and goes into vista.

Now I have probably made an error in configuring the loader for Linux, so I am asking for help from anyone who knows anything about EasyBCD, I'm pretty sure I installed Ubuntu into a totally different parition (but EasyBCD only shows 2 of my supposedly 3 partitions.)  And yes I am new to Linux and was hoping to try it out, but now I can't even boot into Ubuntu anymore.

Any help would be much appreciated.

Thanks

---------------------------------------------------------------------------------------------------------
edit 02/05/08 @ 12:53AM

Thanks Jay and Guru

So I got fed up with the vista boot loader and I got around to re-loading grub and configuring it, but now, when I use GRUB and select Vista, the Vista boot loader pops up now (and apparently it works with linux/xp now -.- go figure).

But a new problem arose, now I have 2 boot loaders and I want to get rid of the vista one, any ideas anyone? Uninstalling EasyBCD did not do the trick.

---

### Post by jaytek13 on 2008-02-02
There is a tutorial here:

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)


Might give some explanation of what went wrong or how to proceed.

---

### Post by Computer Guru on 2008-02-02
If it skips through the dual-boot options then perhaps EasyBCD's timeout is set to zero, or the Vista bootloader needs to be reinstalled.

---

### Post by mmm_unit on 2008-02-05
Thanks Jay and Guru

So I got fed up with the vista boot loader and I got around to re-loading grub and configuring it, but now, when I use GRUB and select Vista, the Vista boot loader pops up now (and apparently it works with linux/xp now -.- go figure).

But a new problem arose, now I have 2 boot loaders and I want to get rid of the vista one, any ideas anyone?  Uninstalling EasyBCD did not do the trick.

---

### Post by e_james on 2008-02-05
I don't know Vista (and I don't want to) but, based on my XP experience, I'm thinking it should be reasonably easy to edit the Vista boot loader to only boot Vista. I think, if there's only one choice, you will normally not see it.

Edit

I believe that the XP or Vista boot loader is always present, even with a fresh one OS installation, (you can't get rid of it); but, if there is only one option, you don't notice it operating.

---

### Post by mmm_unit on 2008-02-06
I don't have a problem configuring the bootloaders, I just want to completely disable the vista bootloader and let grub do the job.  

Currently, Both the vista bootloader and grub are working.

Example: 
I boot up my computer:
GRUB opens: I choose Vista[B]
Vista Bootloader opens: I choose Vista[/B] [COLOR="Red"]<-want to get rid of this step[/COLOR]
Vista Boots

---

### Post by logos34 on 2008-02-07
Grub cannot directly boot windows--vista or XP.  Grub can only chainload it.

But you shouldn't be seeing the vista boot menu, like e_james said, if there's only one choice.  Reinstall EasyBCD--it's the best way to change it.

---


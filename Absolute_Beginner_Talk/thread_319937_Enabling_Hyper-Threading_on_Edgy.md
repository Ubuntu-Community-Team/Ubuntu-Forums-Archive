---
title: "Enabling Hyper-Threading on Edgy"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by illu45 on 2006-12-16
Hi all,

I've been trying to enable hyper-threading on Edgy, with no luck so far :(. I'm running on a 32-bit Intel Pentium 4 2.8 Ghz processor. I've tried following the How-To here: [http://ubuntuforums.org/showthread.php?t=155838&highlight=hyper+threading](http://ubuntuforums.org/showthread.php?t=155838&highlight=hyper+threading) but when I do the "sudo update-grub" step, it removes the changes I made to the menu.lst file. So, when I restart, the System Monitor only shows one processor, which tells me HT has not been enabled. 

Any ideas would be greatly appreciated,

Thanks,
illu45

---

### Post by rodrigo juarez on 2007-03-19
Well, i'm not sure if it's just me but I edited menu.lst to include XP in the boot menu and it worked. I also tried editing and running update-grub and my edits were gone, so I think you could edit the file and leave update-grub alone.
I'm not sure if this is the common procedure tho.

---

### Post by mahiyar on 2007-03-19
I have the same configuration as yours, but I did not have to do anything separately, the HT was on by default. The foremost thing is that  HT should be "ON" in bios first then your operating system will recognize the same.

---

### Post by konst88 on 2007-03-19
Are you using the generic kernel?

---


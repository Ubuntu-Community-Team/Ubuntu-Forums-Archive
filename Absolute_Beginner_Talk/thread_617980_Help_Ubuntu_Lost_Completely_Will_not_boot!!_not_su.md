---
title: "Help Ubuntu Lost Completely Will not boot!! not sure what to do."
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by frame45 on 2007-11-19
ok I here is my system:

Asus A7N8X-E motherboard
AMD Athlon XP 2200+ 1.80Ghz 
1.0Gb Kingston Hyper-X DDR 333 RAM
Western Digital 80Gb Hard drive (Windows XP)
Western Digital 120Gb Hard Drive (Ubuntu 7.10)

I did a clean install of Ubuntu 7.10 Gutsy on the 120gb and it automatically installed GRUB so when I boot up, it goes to a screen and asks if I want to boot: Ubuntu 7.10; Ubuntu 7.10 (recovery mode); other operating systems; windows XP. I has been working fine, I just select Ubuntu and everything was great until yesterday, my computer had been off all day while i was @ work. I came home fired it up and selected Ubuntu 7.10. Then I got this:

[COLOR="Red"]init: unable to execute "/bin/sh" for rcS: No Such file or directory
init: rcS main process (2718) terminated with status 255
init: unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (2719) terminated with status 255 [/COLOR]


I tried to boot into the Recovery mode it didn't do anything (not that I would have known what to do.)  Could I just boot to the live cd and copy the files back into the "/bin/sh" folder?? 

Where do I need to go without have to format or reinstall the system on the drive??

Any help will be greatly Appreciated. Thanks:confused:

---

### Post by Nano Geek on 2007-11-20
> **frame45 said:**
> ok I here is my system:

Asus A7N8X-E motherboard
AMD Athlon XP 2200+ 1.80Ghz 
1.0Gb Kingston Hyper-X DDR 333 RAM
Western Digital 80Gb Hard drive (Windows XP)
Western Digital 120Gb Hard Drive (Ubuntu 7.10)

I did a clean install of Ubuntu 7.10 Gutsy on the 120gb and it automatically installed GRUB so when I boot up, it goes to a screen and asks if I want to boot: Ubuntu 7.10; Ubuntu 7.10 (recovery mode); other operating systems; windows XP. I has been working fine, I just select Ubuntu and everything was great until yesterday, my computer had been off all day while i was @ work. I came home fired it up and selected Ubuntu 7.10. Then I got this:

[COLOR=Red]init: unable to execute "/bin/sh" for rcS: No Such file or directory
init: rcS main process (2718) terminated with status 255
init: unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (2719) terminated with status 255 [/COLOR]


I tried to boot into the Recovery mode it didn't do anything (not that I would have known what to do.)  Could I just boot to the live cd and copy the files back into the "/bin/sh" folder?? 

Where do I need to go without have to format or reinstall the system on the drive??

Any help will be greatly Appreciated. Thanks:confused:You could try that, but beyond that I think it would just be easier to reinstall.

But make sure you do a backup of your data before you reinstall.

---

### Post by frame45 on 2007-11-23
umm i tried to use the cp & mv commmand in terminal to replace the files but I couldn't get it to work so I just backed up files to my windows partition and the reinstalled my system. Wow I sure hope that I don't have to go thourgh that again.

---


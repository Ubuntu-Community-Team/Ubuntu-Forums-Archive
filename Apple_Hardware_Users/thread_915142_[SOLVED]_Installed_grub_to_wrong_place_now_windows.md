---
title: "[SOLVED] Installed grub to wrong place now windows boot loops in grub"
date: 2008-09-09
forum: Apple Hardware Users
---

### Post by kylegio on 2008-09-09
so, i installed grub to wrong place (this is fixed now) but it has over written the windows bootloader (sorry if im using improper terminology) 

when i try to boot windows (in refit or bootcamp by holding option at boot) it loads the grub bootloader, i can select widnows, and it loops back to the grub bootloader .... again again and again

supposedly i can fix this with my windows install CD? but i never get that recovery prompt when i put my windows install cd in, it just loads through until it asks me what hard drive i want to use and asks me to format it 

i kinda have to get this fixed asap, (school and ****) can someone please give me a hand! 

thanks in advance

---

### Post by cyberdork33 on 2008-09-09
When the Windows CD is booting, it will prompt you to hit a key to enter recovery console. I think it is f2 or something.

When you select Windows in the grub menu, it still shows GRUB? If that is the case you might need to checkout the FIXBOOT command too.

---

### Post by caljohnsmith on 2008-09-09
Your situation sounds like the classic case where Grub accidentally got installed to the boot sector of the Windows partition, and that's what causes Grub to loop-back on itself when you try and boot Windows. The way to fix it is with "fixboot" from the Windows CD, like cyberdork33 mentioned. 

But if you can't get your Windows CD into the recovery console to run fixboot, it is possible to do the same operation with "testdisk" in Ubuntu. See [this post]("http://ubuntuforums.org/showthread.php?t=836583&postcount=5") of how to do it, it is quite easy.

---

### Post by kylegio on 2008-09-09
> **caljohnsmith said:**
> Your situation sounds like the classic case where Grub accidentally got installed to the boot sector of the Windows partition, and that's what causes Grub to loop-back on itself when you try and boot Windows. The way to fix it is with "fixboot" from the Windows CD, like cyberdork33 mentioned. 

But if you can't get your Windows CD into the recovery console to run fixboot, it is possible to do the same operation with "testdisk" in Ubuntu. See [this post]("http://ubuntuforums.org/showthread.php?t=836583&postcount=5") of how to do it, it is quite easy.



You are a legend man, thanks... 

literal 45 seconds to fix

---

### Post by cyberdork33 on 2008-09-09
Please mark this thread as solved from the thread tools menu.

---


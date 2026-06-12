---
title: "Trouble Installing/Booting Ubuntu Studio"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by HeyBudItsSteve on 2007-07-08
I have had Ubuntu for a couple of months, however i recently decided to reformat my computer and install Ubuntu Studio. ( i know i didnt have to reformat and install but could have instead just upgraded, but my computer was getting messy) I had no problem downloading, burning, or installing the OS. However, when i try to boot into it from my hard drive when loading the GRUB, i get " error 18" and my computer stops. Please help, i already tried installing it twice, but received the same message. Thanks.

---

### Post by Nekiruhs on 2007-07-08
Error 18 means that GRUB is past the point that your BIOS can boot to. This means you have to make a /boot partition at the beginning of your drive in order for GRUB to boot.

---

### Post by HeyBudItsSteve on 2007-07-08
that makes sense, how big should I make this partition? and do i have to reinstall ubuntu again?

---

### Post by Nekiruhs on 2007-07-08
The partition should be roughly 100Mb. Yes, unfortunately it will mean a reinstall.

---

### Post by HeyBudItsSteve on 2007-07-08
Thanks, it is reinstalling now. However, i didnt know if i should put it as primary or logical, so i just put it as logical, which made sense to me. I'll post if it works or not. Thanks a lot!

---

### Post by ektober on 2008-02-01
I too have problem with booting Ubuntu Studio. When booting, Grub loads but then this come up on the screen:
----------------------------------------------------------------------------------------------------------
[  33.113025]  [<c023fc38>] pnp_chech_irq+0x160\0x170
                                                    
 ---There is a list with similar messages between these two---

[  33.114737]  [<c0105627>] kernel_thread_helper+0x7\0x10
[  33.114815]  ================
-----------------------------------------------------------------------------------------------------------
and last is a blinking prompt and I can do nothing but shut down the computer.

Does anyone have an idea of what to do?

---

### Post by Cayitano on 2008-03-17
Hello ektober,

I found your post by searching for the data  [<c0105627>] .

I could boot up by pressing the escape key and I selected the generic load instead of
Ubuntu 7.10. kernal 2.6.22-14-rt . 

I uninstalled Ubuntu Studio, Kubuntu, Edubuntu and rebooted each time to no avail because the boot down screen was reading the last two packages instead of Ubuntu.

Booting up generic again, I looked for Ubuntu and found a package identified as i386 meta something and installed it.

Boots down and up without needing to press the ESC key as before.

I will post a better description about the cause for this search in the boot forum.

Cayitano

---


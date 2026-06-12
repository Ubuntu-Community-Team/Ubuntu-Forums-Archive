---
title: "Kernel question....."
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Christopher on 2006-12-19
I installed kernel 2.6.15-27-386, i rebooted and everything was fine, i got the nvidia splash screen and when i got to my desktop i didnt have to re-install my nvidia drivers?? I thought i had to re-install my nvidia drivers after every kernel upgrade? One other question, is this kernel im using rather new? Thank you in advance.

---

### Post by pormogo on 2006-12-19
If the Nvidia driver is anything like the fglrx drivers you won't have to reinstall the drivers either. It's a kernel module and not actually compiled into the kernel, the module just loads when the system boots.

type in* dmesg|grep fglrx* at a terminal and you will see the output from the kernel module loading. (replace fglrx with whatever the nvidia driver is called)

---

### Post by Bachstelze on 2006-12-19
No, you don't need to reinstall the nvidia drivers indeed. They're in the restricted-modules package, which was also upgraded to match your new kernel.

As for you question, 2.6.15 is rather new indeed given that the latest version is 2.6.19. If you want a newer kernel though, you can either upgrade to Edgy/Feisty or compile it yourself.

---

### Post by Christopher on 2006-12-19
Ok thank you for the very fast replies, i use Albert Milone's script thats posted here in the forums. Again thank you.

---


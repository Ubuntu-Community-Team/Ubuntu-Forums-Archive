---
title: "GG stalls during boot"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by keych on 2007-11-25
I installed Gutsy yesterday and have been doing fairly well with it as a fairly technical Windows user new to Linux.  I've got my Acer Aspire 3023 wireless up and running (apparently its a difficult one to do) and have Compiz Fusion going, but now I am having problems booting and shutting down.

On boot, I get the splash screen (I've modified the grub install and splash) but then it drops to a flashing cursor on the top left of the screen. I've found that typing exit and pressing enter lets it carry on.

On shut down / reboot, It gets to a flashing cursor again, but nothing seems to let it carry on and I have to hard power off (hold the power button).

Here is my grub script for booting Gutsy:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=38a775d6-92c3-4f5e-8d45-38fe2ad7f1bc ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Can anyone help me find what could be causing this?

---

### Post by keych on 2007-11-26
I fixed it - it was the script I added for starting wireless on boot up.

Changed it to the correct script at [http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi](http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi)

---

### Post by Tom Mann on 2007-11-26
Good good :)

If you're happy could you mark the title of this conversation as fixed? It'll help us helpers :)

---

### Post by keych on 2007-11-26
indeed I will.

Thanks for looking

---


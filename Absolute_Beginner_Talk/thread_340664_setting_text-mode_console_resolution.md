---
title: "setting text-mode console resolution"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by dimovich on 2007-01-17
Hello,

How to set a smaller font size for the text-mode console. Or, is it a way to set the resolution of the text mode?

Thanks!

---

### Post by taurus on 2007-01-17
You can add "**vga=791**" in the kernel entry (near or at the end) in /boot/grub/menu.lst.

```
sudo nano -w /boot/grub/menu.lst
```

---

### Post by dimovich on 2007-01-17
**vga=791** seems too small... What other modes besides this one are there?

(added)
I found that 788 mode works just fine for me. Now, how do I set a higher refresh rate for this mode (now is 60Hz)?

---

### Post by pmasiar on 2007-01-17
sudo dpkg-reconfigure xserver-xorg see:

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

---

### Post by K.Mandla on 2007-01-17
There's a brief chart here that might help.

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_Change_Font_Size_During_Boot_Framebuffer_Resolution](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_Change_Font_Size_During_Boot_Framebuffer_Resolution)

There are some more obscure options, depending on the color depth you want. But those are the most common. ;)

---

### Post by dimovich on 2007-01-18
> **pmasiar said:**
> sudo dpkg-reconfigure xserver-xorg see:

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

My X.Org Server works just fine (1024x768x24 at 100 Hz), but I would like to have a higher refresh rate (>60Hz) for text-mode console.

---


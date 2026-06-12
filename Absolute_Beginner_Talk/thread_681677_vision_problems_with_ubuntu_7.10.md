---
title: "vision problems with ubuntu 7.10"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by madtekrunner on 2008-01-29
Hello all,
   I am having issues installing ubuntu 7.10 on an IBM 600 P2 with 348mb ram and a 40GB HD.  I know the screen will do 800X600, however I am not able to get the base of the screen after selecting the country.  Is there any one that can help me resolve this issue?

madtekrunner

---

### Post by spiderbatdad on 2008-01-29
load the cd again. and when you get to the Install options screen, hit F6. Then I think you can hit F1 to read more, and F6 again for examples of boot parameters. I'm thinking you would need to add vga=771 to the end of the kernel line. You get back to the install options page with esc. If this works, after the installation, I imagine you would need to add the same parameter in /boot/grub/menu.lst  to the end of the kernel line shown below:
```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash** vga=771**
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot
```

You can see, in bold, where I added the parameter to the end of the kernel line. This is done with a text editor after your os is installed. For example, You would open your terminal interface under Applications>>Accessories>>Terminal. Then you would input ```
gksu gedit /boot/grub/menu.lst
```After making changes, you save...close...exit terminal. (that is a small "L" not a 1 in .lst.) Note: your menu.lst will not look exactly like mine. Your are looking for the first title block that doesn't contain hash marks (#), often called comments. Your first title block will probably be directly under a line that looks like this:## ## End Default Options ##

---


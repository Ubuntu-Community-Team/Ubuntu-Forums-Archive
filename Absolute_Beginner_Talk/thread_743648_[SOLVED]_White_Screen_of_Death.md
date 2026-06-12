---
title: "[SOLVED] White Screen of Death"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Promaster91 on 2008-04-02
Ubuntu recently wanted to install some updates on my computer. I installed the updates and it wanted to restart the computer. When I restarted the computer, I knew something was wrong when the Grub loader showed two options to load Ubuntu. They both where the same version and the same Linux kernel. When I load the first one it got to the login screen. When I entered my username and password and it did the login noise. It started to show my toolbar when the whole screen when white!! I started it in recovery mode. No luck it did the same thing. So, I tried the second option on the Grub loader. It worked. So my question is, Does anybody know what happen and how I get only one option for Ubuntu on the Grub loader?

---

### Post by markp1989 on 2008-04-02
open terminal 
 
and enter
```
gksu gedit /boot/grub/menu.lst
```

and comment out or delete the entry you dont want

---

### Post by Promaster91 on 2008-04-02
Ok, this is weird it seemed to update the kernel. What should I do?
```

title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro quiet splash
initrd		/boot/initrd.img-2.6.24-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro single
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by ghost_ryder35 on 2008-04-02
comment out the one that doesnt work 
i.e.
```

##title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic
##root		(hd0,3)
##kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro quiet splash
##initrd		/boot/initrd.img-2.6.24-14-generic
##quiet

##title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic (recovery ##mode)
##root		(hd0,3)
##kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro single
##initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=bd852857-4ff8-4c59-9ef0-d8133171a356 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by Mogurijin on 2008-04-02
This is odd. You are not the first user you went to download some updates and got a distro upgrade...

I don't know if people are just making a mistake with updating or what... (I'm sure on the process for a distro upgrade with out a clean install)

I haven't had this problem since right now I'm on Windows (yes it breaks my heart :cry:) until 8.04.

---

### Post by Promaster91 on 2008-04-02
Ok, I did the commenting out part. However isn't that just hiding the problem. How do I get rid of the updated kernel?

---


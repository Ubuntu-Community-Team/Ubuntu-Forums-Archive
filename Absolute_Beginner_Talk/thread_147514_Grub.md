---
title: "Grub"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-20
Why do I have 2 Kernals listed when I boot?

```

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

```

Do I need the older one and it's recovery and if not how do I remove it?

---

### Post by Brunellus on 2006-03-20
you probably upgraded the kernel recently.  

I have been able to remove old kernel images usings apt/synaptic;  that takes care of grub's menu.list automagically.

---

### Post by jorn on 2006-03-20
You does not need the old one which is not automatically removed if someone still wants to use it if something doesn't work with the new one. But In my case it was save to remove it. Type in terminal:
sudo gedit /boot/grub/menu.lst
And remove it.
Jorn

---

### Post by bluevoodoo1 on 2006-03-20
Or for whatever reason you want to keep the old ones and just tidy up GRUB, place #'s in front of each line of the old kernel info...

#title		Ubuntu, kernel 2.6.12-9-386 
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-9-386
#savedefault
#boot

---

### Post by Lonergan on 2006-03-20
If grub is not listed in the /boot directory where might it be stored?  I had a similar problem, recently installing 2.6.15-18-amd64-k8 but it doesn't come up in my Grub list, after searching via find ./ *grub  I didn't get any returns.  I know it must be here somewhere.

---


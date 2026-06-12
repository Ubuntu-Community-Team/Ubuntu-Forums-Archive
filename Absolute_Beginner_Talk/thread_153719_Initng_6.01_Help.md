---
title: "Initng 6.01 Help"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-04-01
I'm following the Initng Tutorial in the Ubuntu Wiki. I got it installed and all that. Now I'm at the part where it says "edit your GRUB list: sudo gedit /boot/grub/menu.lst Make a duplicate Ubuntu entry and rename its title to something like Ubuntu (InitNG). In the kernel line add init=/sbin/initng"

Where is the kernel line ? Can someone who installed it post their menu.lst so I can see where it is. I have had no problem in the past installing it.

---

### Post by xXx 0wn3d xXx on 2006-04-01
does anyone know. I need to add it to the kernel line.

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=MasterChief1234]does anyone know. I need to add it to the kernel line.[/QUOTE]
Can anyone help ? I've bee trying to get help for over 5 hours.

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=MasterChief1234]Can anyone help ? I've bee trying to get help for over 5 hours.[/QUOTE]
Anyone ?

---

### Post by idlewild on 2006-04-01
Find the region at the bottom of /boot/grub/menu.lst that look like this
```
title           Ubuntu, kernel 2.6.15-19-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-19-686 root=/dev/hda3 ro quiet
initrd          /boot/initrd.img-2.6.15-19-686
savedefault
boot

```
Copy and paste and append the kernel line with init=/sbin/initng and change the title line to something different
```
title           Ubuntu, kernel 2.6.15-19-686 (InitNG)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-19-686 root=/dev/hda3 ro quiet init=/sbin/initng
initrd          /boot/initrd.img-2.6.15-19-686
savedefault
boot

```

Do not copy and paste this. You have to modify your own as you will likely have a different kernel and different kernel options. Initng is not very widely used so you would have more luck asking for help on an existing thread open for initng support.

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=idlewild]Find the region at the bottom of /boot/grub/menu.lst that look like this
```
title           Ubuntu, kernel 2.6.15-19-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-19-686 root=/dev/hda3 ro quiet
initrd          /boot/initrd.img-2.6.15-19-686
savedefault
boot

```
Copy and paste and append the kernel line with init=/sbin/initng and change the title line to something different
```
title           Ubuntu, kernel 2.6.15-19-686 (InitNG)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-19-686 root=/dev/hda3 ro quiet init=/sbin/initng
initrd          /boot/initrd.img-2.6.15-19-686
savedefault
boot

```

Do not copy and paste this. You have to modify your own as you will likely have a different kernel and different kernel options. Initng is not very widely used so you would have more luck asking for help on an existing thread open for initng support.[/QUOTE]

Thanks but I got it to work by myself. I really wasn't thinking. I appreciate you trying to help :)

---


---
title: "Advantages of Kernel 16?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-06-18
Any advantages to kernel 16? I just updated to it, and when I boot I get to the kubuntu loading bar, and nothing happens till it goes to a white blinking line. The 15 kernel works fine. Just wondering if there were any advantages to the kernel so I can evaluate if its worth trying to fix it (BTW, I've done the 15 - 16 update about 4 times before on this machine, previous installs of 7.04, and had no problems, the only difference now is that I installed from the DVD, not the cd).

---

### Post by Bachstelze on 2007-06-18
[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_2.6.20.16.28.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_2.6.20.16.28.1/changelog)

Nothing critical, as you can see.

---

### Post by hardyn on 2007-06-18
if your grub references the disks staticly (/dev/hdx) you will have trouble with the update
you MUST have your drives referenced using the UUID system.

something to check.

---

### Post by Nekiruhs on 2007-06-19
UUID? Never heard that term before. If I post a stanza from my menu.lst  can you tell me if it uses UUID or static?
```

#title		Ubuntu, kernel 2.6.20-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.20-16-generic #root=UUID=5f132675-c46a-4821-b27f-8a23de01c57a ro quiet splash
#initrd		/boot/initrd.img-2.6.20-16-generic
#quiet
#savedefault

```
```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5f132675-c46a-4821-b27f-8a23de01c57a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```
```
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
Thats a synopsis of my Menu.lst, the 16 kernel is commented out so I don't boot that. The 15 kernel works fine, and so does XP.

---

### Post by hardyn on 2007-06-19
Hmm, its actually looks okey... 

It was a suggestion, as it was a really common problem; sorry i couldn't be more help.

---


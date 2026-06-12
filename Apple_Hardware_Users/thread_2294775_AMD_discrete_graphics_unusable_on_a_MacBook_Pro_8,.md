---
title: "AMD discrete graphics unusable on a MacBook Pro 8,2"
date: 2015-09-13
forum: Apple Hardware Users
---

### Post by cialu on 2015-09-13
I have installed Ubuntu 15.04 on a MacBook Pro 8,2 with a proper EFI  single boot. All works like a charm and the boot process is really fast,  I'm really satisfied.


  I have only one issue: I can use Ubuntu only with the Intel  integrated graphics card and with the AMD discrete graphics card turned  off. I mean with this trick in the grub:
```

outb 0x728 1
outb 0x710 2
outb 0x740 2
outb 0x750 0
```


I have installed the AMD Catalyst driver but I'm unable to config it  because the card is turned off. If I boot without the grub trick, I have  a black screen result. If I boot with nomodeset in grub, I have a black  screen result too. So, is there a way to use also the discrete graphics with Ubuntu on the MacBook Pro 8,2?

I have also added a second choice to grub menu. It's intended to boot only with discrete graphics card. I have removed the list ```
outb 0x...
```and I have added the kernel options ```
i915.modeset=0 radeon.modeset=1
```but the result is the same: only a black screen. After all, I think  that MacBook Pro 8,2 is usable only with Intel Integrated graphics and,  for me, this is a big problem because that means I'm not able to use an  external monitor. (Only the Radeon seems connected to the external  display port).

I have read a lot on forums and faq, but no solution work for me. Any idea?

---

### Post by tom210 on 2015-10-02
Hello, 
I have the same problem. I would like to enable the AMD GPU so I can use an external monitor. I tried a lot of different methods I found on the internet but with out success . most of them are referring to this post: [http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775) 
unfortunately I just can´t seem to get it to work, I sure someone (much smarter then me) got it to work and I hope that someone reads this thread and can explain the steps I need to follow to get it to work also.

best regards Tom

---

### Post by denics on 2015-10-16
I really hope somebody will find a solution to this :( AMD support is really bad for linux, My MacPro 6.1 is almost unusable with linux

---

### Post by QIII on 2015-10-16
AMD support for Linux is not bad, denics.  You are running Linux on Apple hardware.  That seems to be the key here.

Did you try as I suggested?

---

### Post by denics on 2015-10-21
Hi @QIII, unfortunately I did not had the time yet, but I will keep you informed as soon as I do something! Thanks!

---


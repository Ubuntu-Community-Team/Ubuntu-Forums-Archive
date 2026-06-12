---
title: "CD Not Booting on Macbook Intel"
date: 2011-03-04
forum: Apple Hardware Users
---

### Post by GotWookie on 2011-03-04
Hello, I am new to Ubuntu, got it running on my Windows, and I love it. Now i try to install it onto my Mac, and I get problems. It boots the purple screen with the little box, and man on it, but then it goes to a black screen and nothing happens. I know it is not the disk because it worked perfect in my windows, and suggestions? I have the white macbook by the way.

---

### Post by GotWookie on 2011-03-04
anyone know, please, i really need help. It it the fact that it does not have the drivers for my GFX card? Mine is a NVIDIA GeForce 9400M. Please reply, i need help.

---

### Post by alexmurray on 2011-03-05
Try hitting escape when the logo of the man and keyboard shows up, then hit F6 for more options and edit the boot command line and remove the words

```
splash quiet
```

(but leave the double dash --) at the end

Then boot - you should see a bunch of debugging messages scroll past - if the boot still freezes but you now see a message something like:

```
nouveau: PRAMIN flush timeout
```

Reboot and again edit the boot commandline (hit escape, press F6 etc)

And add the option:

```
nouveau.noaccel=1
```

This should allow you to boot now. This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393)  and [https://bugs.freedesktop.org/show_bug.cgi?id=27501](https://bugs.freedesktop.org/show_bug.cgi?id=27501)

---

### Post by macbookproi7 on 2011-03-06
just quickly I'll ask... have you tried being patient and just waiting a while as it tries to boot? I know a few times when I was booting from cd it took AAGES. eventually it loaded.. a couple of times I had to turn my commputer off and start again. I think sometimes the CD rom just didn't read the disc properly.

---


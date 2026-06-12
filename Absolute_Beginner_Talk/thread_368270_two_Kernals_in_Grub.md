---
title: "two Kernals in Grub"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-23
i have installed ubuntu 6.10 from cd iso i.e. ubuntu6.10-desktop-i386.iso and it shows two kernals in boot menu:
 
upon checking in terminal after boot i get this:

```

waqas@black-cat:~$ uname -r
2.6.17-10-generic

```
and
```

waqas@black-cat:~$ uname -r
2.6.17-11-generic

```

Why??

---

### Post by Luk0r on 2007-02-23
Kernel update you downloaded when you initially booted, you could always edit your GRUB boot config file and remove the older version if you wanted to.

---

### Post by shoaibi on 2007-02-23
but i did not update kernal afaik

---

### Post by nickoli_02 on 2007-02-23
When the linux kernel is updated, a menu entry is automatically added to the grub menu list. It's safe to remove the old kernel entry if you like. 

```
gksudo gedit /boot/grub/menu.lst
```

The menu entries are at the bottom of the file. You can either delete the entries or simply comment them out with #'s

---

### Post by shoaibi on 2007-02-23
**_[COLOR="Red"]from were did it appear without any manual kernal updates[/COLOR]_**

---

### Post by ComplexNumber on 2007-02-23
its not possible that 2 kernels appear without you having updated the kernel. have you not done any update whatsoever since you first installed ubuntu?

---

### Post by Tomosaur on 2007-02-23
You may aswell just accept that you updated the kernel, that's the only way it would have happened. Open up a command line and type:
```

ls /boot/

```

You will see the various files relating to the new kernel there.

Nobody is forcing you to use it - you can keep using the older kernel if you like.

---

### Post by shoaibi on 2007-02-23
Welll i agree, but i didnt do aything except adding repo, installing Easyubunutu, SAMBA, installing vlc, and giving proxy in firefox......
i can tackle with what happend or not, that's not the question.
the question is WHY???
from where it appeared without any updates done by me, whereas no body else uses the syetm...
Experienced the same thing on two different brand and spec PCs. Using VMware.

---

### Post by Tomosaur on 2007-02-23
> **shoaibi said:**
> Welll i agree, but i didnt do aything except adding repo, installing Easyubunutu, SAMBA, installing vlc, and giving proxy in firefox......
i can tackle with what happend or not, that's not the question.
the question is WHY???
from where it appeared without any updates done by me, whereas no body else uses the syetm...
Experienced the same thing on two different brand and spec PCs. Using VMware.

I'll repeat - there is no possible way for this to happen unless you download and install the new kernel. Kernel updates appear as ordinary updates - it's entirely possible that you installed some updates without realising that the new kernel was included - I've done it a number of times.

The only other way for this to happen is if you have another linux installation on a different partition - in which case you may be using the menu.lst from **that** installation.

---

### Post by ComplexNumber on 2007-02-23
> **shoaibi said:**
> Welll i agree, but i didnt do aything except adding repo, installing Easyubunutu, SAMBA, installing vlc, and giving proxy in firefox......
i can tackle with what happend or not, that's not the question.
the question is WHY???

why? because linux keep the old kernel just in case. a safety precaution, if you will. imagine if you updated your kernel and it turned out not to work with various hardware that you have. you would like to have your previous kernel to fall back on, wouldn't you? well, thats the reason. its just another level of protection.
i would advise that a user keeps the old kernel for about 3-5 days to see if all is good with the new kernel, then delete the old kernel via synaptic.

---

### Post by shoaibi on 2007-02-23
hmmmmmm oh....... i did select mark all updates in synaptic......
Okies i will delete that...

---


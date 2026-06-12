---
title: "I can't find the kernel headers for 2.6.12-9-386"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by dan fisher on 2006-04-23
I can only see them for 2.6.11 on ubuntu packages.

Can anyone help?

I can't use apt-get (need kernel headers to compile driver to connect).

---

### Post by gr0kzer0 on 2006-04-23
Are you using Breezy? They should have come with the default installation. If you go to Synaptic and mark it for installation, it will be done for you.

PS: Called linux-headers-2.6.12-9-386 in Synaptic, I believe.

---

### Post by dan fisher on 2006-04-23
there you go - i thought synaptic was a website

ty very much

---

### Post by adamkane on 2006-04-23
kernel 386 is for older legacy PCs (Intel Pentium Pro or 486).

You may want to install kernel that is appropriate for your hardware:

Intel Pentium (Other than Pro or 486):

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

```

AMD K Series (Duron, Athlon, Sempron):
 
 ```

 sudo apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7
 
```

Reboot.

---


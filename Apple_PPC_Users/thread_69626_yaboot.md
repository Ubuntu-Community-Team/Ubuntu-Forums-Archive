---
title: "yaboot"
date: 2005-09-27
forum: Apple PPC Users
---

### Post by MArco_ubuntu on 2005-09-27
Hi!
I want to start to compile my kernel (ibook 12" g3 500 dual usb)
I want to know how to use more than 1 kernel in yaboot because I need to test some time my kernel and I doesnt know if it run correctly from the first time


Thanks alot!


Marco

ps: maybe sombosy have a config for kernel whit my ibook ? :)

---

### Post by stuporglue on 2005-09-27
No good kernel config for you, but here's how to do yaboot....

edit /etc/yaboot.conf

Copy one of the sections like this

```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

```

and change the image to point at your new kernel, the label to whatever you want to show up in yaboot. 

Add a line root=/dev/blah if the generic one near the top of yaboot.conf isn't the same for this kernel.

When you're done, run "ybin -v" and it'll apply the changes to the boot partition.

---


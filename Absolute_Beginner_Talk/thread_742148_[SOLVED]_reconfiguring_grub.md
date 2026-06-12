---
title: "[SOLVED] reconfiguring grub"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by djbsteart1 on 2008-04-01
I have a corrupt install on hda6 after a kernel update, but I still have a old install on hda5, what I need to do is set up the grub that is installed on the MBR of hda5, I tried using root (hda0,5) but I get an error saying that the drive doesn't exist. 
So what my problem is, is that I don't know what hda5 is in grub talk. Once I have that i can use setup (hdx,x) to install the setup I need. 

Thanks for the help.

---

### Post by Duck2006 on 2008-04-01
Some reading on grub that may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by smurphy_it on 2008-04-01
I believe it is minus 1.

Thus HDA5 would be HDA(0.4)

---

### Post by ghost_ryder35 on 2008-04-01
> **djbsteart1 said:**
> I have a corrupt install on hda6 after a kernel update, but I still have a old install on hda5, what I need to do is set up the grub that is installed on the MBR of hda5, I tried using root (hda0,5) but I get an error saying that the drive doesn't exist. 
So what my problem is, is that I don't know what hda5 is in grub talk. Once I have that i can use setup (hdx,x) to install the setup I need. 

Thanks for the help.

do you have a live cd?  you could boot onto that and see what the drive is being labled and fix grub

mine looks like this
```

title		Ubuntu 7.10 64 bit, kernel 2.6.22-14-generic
root		**(hd0,2)**
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c228e468-eaaa-4704-9b94-a77f22a54879 ro
initrd		/boot/initrd.img-2.6.22-14-generic

```

mine is showing up as zero not "a", maybe trying "hd0,5" would work

---

### Post by djbsteart1 on 2008-04-01
This was from a live cd.
No worries, I got it fixed with slitux, just installed that then reinstalled ubuntu, one spare partition once I got data out. 

Thanks for the help though.

---


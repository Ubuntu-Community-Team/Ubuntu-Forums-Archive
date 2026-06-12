---
title: "Intel GRUB Bootsplash"
date: 2007-06-14
forum: Art &amp; Design
---

### Post by apoorvkhurasia on 2007-06-14
Hi

I made this GRUB bootsplash that displays the intel inside logo. Use it if you like. I have named it as intelsplash.xpm.gz so you might have to edit your grub.conf accordingly.
Hence if you place this image in your /boot/grub directory and your root is the partition 1 of disk 1 then make sure this line appears in your /boot/grub/menu.lst
```

splashimage (hd0,0)/boot/grub/intelsplash.xpm.gz

```Note that if your root partition is on other partition than what is mentioned above you need to change this line accordingly. Example if root is /dev/hda2 then use
```
(hd0,1)
```About foreground and background colors. I am using (and liking it too!!!)
```

I am using
[code]
foreground 44aa55
background 000000

```Enjoy!!!

---

### Post by webdesigncompany on 2008-01-03
hi i have allways wondered can you make animated bootsplash in some way?

does somebody know?

---

### Post by smartboyathome on 2008-01-03
> **webdesigncompany said:**
> hi i have allways wondered can you make animated bootsplash in some way?

does somebody know?

You can't unless you use RHGB (which basically makes a graphical session while you boot up). Otherwise, you can't.

---


---
title: "Can I copy a kernel?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by opticyclic on 2006-10-15
Is the only place my kernel stored in /boot?
I can't get into my system and I think it might be to do with the kernel being removed somehow.
I can access the files via the LiveCD.
Could I copy the contents of /boot from the LiveCD onto my main installation /boot?

---

### Post by Kateikyoushi on 2006-10-15
What makes you think it has to do something with your kernel  ?
What is the error message you receive during boot ?

---

### Post by opticyclic on 2006-10-15
The reason that I am suspecting the kernel is that my system was fairly up to date.
Now, the contents of my /boot directory are```
**ubuntu@ubuntu:/mnt/old/boot$ ls**
cboot.b        debian.bmp        initrd-2.6.10.gz.inf   sarge.bmp
coffee.bmp     debianlilo.bmp    linux-swap.swp         sid.bmp
config         grub              los-bootsplash.bmp     System.map-2.6.10
config-2.6.10  initrd-2.6.10.gz  los-bootsplash.xpm.gz  [SIZE="2"][COLOR="Red"]vmlinuz-2.6.10[/COLOR][/SIZE]
ubuntu@ubuntu:/mnt/old/boot$
```That kernel should be at least 2.6.15

Unless I am looking in the wrong place.

I get things like
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by taurus on 2006-10-15
You should look at your /boot/grub/menu.lst to see what's wrong with it!!!  And no, your kernel is vmlinuz-2.6.10.

---

### Post by opticyclic on 2006-10-16
Im having troubles with my menu.lst [here]("http://www.ubuntuforums.org/showthread.php?t=278083")
Isn't vmlinuz-2.6.10. older than what is on the LiveCD?
How is that possible?
Surely it would be at least the same since the LiveCD is what I used to install....

---

### Post by opticyclic on 2006-10-20
If anyone is interested, not surprisingly copying the image doesn't work.
Forcing an installation of the kernel in the boot directory following this info might though
[http://ubuntuforums.org/showpost.php?p=1431609&postcount=50](http://ubuntuforums.org/showpost.php?p=1431609&postcount=50)

However, I am having to compile my own kernel following this info
[http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657)

---

### Post by az on 2006-10-20
Why do you have a sarge kernel in your ubuntu install?

---

### Post by CatKiller on 2006-10-20
I've never tried this, or anything like it, but you could boot from the live cd, then use pivot_root to change the filesystem to one that's based on the Ubuntu install on the hard drive, and then ```
sudo aptitude install linux
``` to get the latest version of the kernel installed properly.

---


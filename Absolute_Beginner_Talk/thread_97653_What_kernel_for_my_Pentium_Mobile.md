---
title: "What kernel for my Pentium Mobile?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by jriff on 2005-12-01
Hi All!

I have a IBM T43p with a Pentium Mobile processor. Should I get the 686 or the 386 kernel?

And how do I remove the old kernel when I have tested that the new one is working? Both from the disk and from GRUB.

- Jacob

---

### Post by ed_d on 2005-12-01
Dont remove, just comment out of menu.lst

---

### Post by arpunk on 2005-12-01
The 686 kernel will do it just fine, just leave the 386 (default installation) just in case something goes wrong, then you can easily boot the default kernel and fix it.

Grub gets updated everytime you add or remove a kernel from apt or synaptic, just make sure it works (test it) before you remove the old one.

---

### Post by jriff on 2005-12-01
Thanks - I am getting the 686-kernel now.

I REALLY want to delete kernels :-) The thing is that I have compiled a kernel myself and it dosn't work... so I want to remove it.

BTW. I have my NTFS-disk mounted in /media/sda1 but I can't access it:

dr-x------  1 root root 4096 2005-11-30 11:51 sda1

Why is it owned by root? My fstab says: 

/dev/sda1       /media/sda1     ntfs    defaults        0       0

- Jacob

---

### Post by arpunk on 2005-12-01
[QUOTE=jriff]Thanks - I am getting the 686-kernel now.

I REALLY want to delete kernels :-) The thing is that I have compiled a kernel myself and it dosn't work... so I want to remove it.

BTW. I have my NTFS-disk mounted in /media/sda1 but I can't access it:

dr-x------  1 root root 4096 2005-11-30 11:51 sda1

Why is it owned by root? My fstab says: 

/dev/sda1       /media/sda1     ntfs    defaults        0       0

- Jacob[/QUOTE]
Heres my ntfs entry in /etc/fstab:
```
/dev/sda1       /media/sda1     ntfs    auto,ro,exec,users,dmask=000,fmask=111,nls=utf8,umask=0222 0       0
```
I dont want write access though, so thats why its *ro*. Once modify try:
```
sudo umount -a
```
And
```
sudo mount -a
```
And dont worry about the "cannot umount..." error messages. Once all disks got remounted, try access your windows partition with nautilus (assuming you running gnome) and enjoy ;)

---

### Post by dabear on 2005-12-01
Replace that line in /etc/fstab with ```

/dev/sda1       /media/sda1  ntfs    nls=utf8,umask=0222 0       0

```
then do a
```
sudo umount /dev/sda1
``` folowed by a ```
sudo mount -a
```
Every user will now have readonly access to /meda/sda1

---

### Post by jriff on 2005-12-01
Great! Thanks to the both of you! I can now read from my NTFS-partition. 

But none of you answerd how I could delete my kernels :-)

---

### Post by arpunk on 2005-12-01
[QUOTE=jriff]Great! Thanks to the both of you! I can now read from my NTFS-partition. 

But none of you answerd how I could delete my kernels :-)[/QUOTE]
lol, if you made the kernel with *kernel-package*, you should be able to delete it with synaptic and grub will update after that, nothing to worry about.

---

### Post by jriff on 2005-12-01
Thanks! It is removed now.  Nice to free up some diskspace :-)

---


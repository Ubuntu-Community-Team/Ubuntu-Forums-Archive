---
title: "Correct layout of /boot and yaboot.conf"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by atarimike on 2006-06-18
I've been messing with my own custom kernel, and I've messed up the symlinks and /etc/yaboot.conf file.
Can anyone tell me what the appropriate symlinks are supposed to look like in /boot, and what the default yaboot conf is? I want everything to be like new again so the installer won't accidentally mess something up.

Thanks, Mike

---

### Post by tidris on 2006-06-18
[QUOTE=atarimike]I've been messing with my own custom kernel, and I've messed up the symlinks and /etc/yaboot.conf file.
Can anyone tell me what the appropriate symlinks are supposed to look like in /boot, and what the default yaboot conf is? I want everything to be like new again so the installer won't accidentally mess something up.

Thanks, Mike[/QUOTE]
What do you have in /boot right now?
What do you have in yaboot.conf right now?
Did you know you need to run ybin after editing /etc/yaboot.conf in order for the changes to take effect?

---

### Post by atarimike on 2006-06-18
[QUOTE=tidris]What do you have in /boot right now?
What do you have in yaboot.conf right now?
Did you know you need to run ybin after editing /etc/yaboot.conf in order for the changes to take effect?[/QUOTE]

Right now I don't have any symlinks in /boot.
I just want to know what its supposed to look like, like what /boot/vmlinux is supposed to point to, like the most recent kernel, and what vmlinux-old points to, etc.
My setup work correctly currently.

---

### Post by tidris on 2006-06-19
[QUOTE=atarimike]Right now I don't have any symlinks in /boot.
I just want to know what its supposed to look like, like what /boot/vmlinux is supposed to point to, like the most recent kernel, and what vmlinux-old points to, etc.
My setup work correctly currently.[/QUOTE]
The answer depends on what your yaboot.conf file looks like.
In my yaboot.conf I have this

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

In there you can see which links my yaboot configuration is looking for: /boot/vmlinux, /boot/initrd.img, /boot/vmlinux.old, /boot/initrd.img.old. 
The vmlinux and vmlinux.old links point to vmlinux-xxxxxx files. The initrd.img and initrd.img.old links point to the matching initrd.img-xxxxxxx files.

---

### Post by BoneKracker on 2006-06-20
Just recreate the symlinks based on the backup you made of your yaboot.conf file before you started editing it.

---


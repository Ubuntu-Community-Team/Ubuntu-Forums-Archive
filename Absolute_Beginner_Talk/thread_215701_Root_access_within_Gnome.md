---
title: "Root access within Gnome"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by terrysalmi on 2006-07-14
Hi there, if there's a better place for this, please move it, i'm new to Ubuntu/Linux.  

I'm trying to access my Windows partition to copy some music over.  I mounted the partition alright using 

```
sudo mount -o ro -t ntfs /dev/hda1 /mnt
```

And can access it using sudo bash from the terminal, but when I try to access /mnt using "computer" in the GUI, I get access denied.  

How can I give my user name "root" access to be able to access /mnt?

Thanks

---

### Post by NESFreak on 2006-07-14
check the systemdocumentation--> ubuntu-desktopmanual--> configuring your system--> Partitions and Booting

for getting root acces in nautilus you could try alt-F2 and enter "gksudo nautilus"

---

### Post by aysiu on 2006-07-14
Try this instead: ```
sudo umount /dev/hda1
sudo mount -t ntfs /dev/hda1 /mnt -o nls=utf8,umask=0222
```

---

### Post by terrysalmi on 2006-07-14
Aysiu, thanks a lot, it worked :)

I'm sitting in a Unix class right now where we're using Ubuntu instead of 'strict' unix and I just brought my laptop in which I put ubuntu on so I can mess around on it during class and try to figure more things out.  My instructor was able to explain the reasoning behind the umask code and why it works.

---


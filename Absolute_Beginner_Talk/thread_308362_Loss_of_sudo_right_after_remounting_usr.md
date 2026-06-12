---
title: "Loss of sudo right after remounting /usr/"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by inkybutton on 2006-11-28
Hi,
I am trying to upgrade to 6.10 aka. Edgy. I don't have much space left in my root partition so I decided to mount another partition to my /usr directory. After copying all the files of /usr/ to partition hda9, I deleted all /usr/ files (under Recovery Mode) and edited /etc/fstab and /etc/mtab so /dev/hda9 mounts at /usr directory. After rebooting, everything seems to work fine until I realize that I lost my sudo right! This is what happens when I type, for example,

 $ sudo apt-get install audacity
 sudo: must be setuid root

This means I can't even go to "Users and Groups" to change my rights back to sudo status! Help...

---

### Post by taurus on 2006-11-28
At a prompt (terminal), see what groups you belong to!

```
groups
```

---

### Post by mssever on 2006-11-28
Reboot in recovery mode. You can fix the permissions from there. ```
chown root:root /usr/bin/sudo && chmod +s /usr/bin/sudo
```
Note that unfortunately, it's likely that you messed up your system more than just sudo. When you're copying system files, you should use cp -a. Otherwise, you'll end up with messed up permissions, symlinks, etc.

---

### Post by inkybutton on 2006-11-28
> **mssever said:**
> Reboot in recovery mode. You can fix the permissions from there. ```
chown root:root /usr/bin/sudo && chmod +s /usr/bin/sudo
```
Note that unfortunately, it's likely that you messed up your system more than just sudo. When you're copying system files, you should use cp -a. Otherwise, you'll end up with messed up permissions, symlinks, etc.

Thanks! I can now run superuser apps now. But, I don't need to enter my password now! = I am root? I would much prefer it if I use sudo with password...

---

### Post by mssever on 2006-11-28
> **inkybutton said:**
> Thanks! I can now run superuser apps now. But, I don't need to enter my password now! = I am root? I would much prefer it if I use sudo with password...

You can find out who you are by typing whoami or id -un. Use visudo to edit sudo settings.

As I said earlier, it's probable that you messed up other stuff in the process of moving /usr. Who knows what could be truly wrong?

---

### Post by inkybutton on 2006-11-28
> **mssever said:**
> 
As I said earlier, it's probable that you messed up other stuff in the process of moving /usr. Who knows what could be truly wrong?

Fine! It's all my fault.[-( 

Well I copy the files via Nautilus, so blame it on the GNOME team...:) 

Also I am upgrading to 6.10 so I hope that fixes the system...

Thanks again!

---

### Post by mssever on 2006-11-28
> **inkybutton said:**
> Fine! It's all my fault.[-( 

Well I copy the files via Nautilus, so blame it on the GNOME team...:) 

Also I am upgrading to 6.10 so I hope that fixes the system...

Thanks again!

Hopefully the upgrade fixes it. There have been several threads about Nautilus and its less-than-stellar performance in copying files in certain situations. I personally use the command line for all that stuff (but then, I use the command line for most things), but it's a shame that Gnome doesn't have a better file manager. I certainly wouldn't trust Nautilus for anything critical.

---

### Post by adam.tropics on 2006-11-28
I suppose if you really wanted you [could always change file manager]("http://www.psychocats.net/ubuntu/nonautilusplease"). Not for me, but it is increasingly it seems, being done.

---


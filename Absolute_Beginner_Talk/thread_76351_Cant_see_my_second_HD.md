---
title: "Cant see my second HD"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by S70P on 2005-10-15
Well I had located my seconds SATA hard drive for about a day and then I was messing around with settigns and somhow it got lost, dont ask me what I did. I ahve tried to unmount it and then try to remount it but it always says it is busy. I've tried different directories to put it in but ntohign works, i've read everything on ubuntuguide.org and i couldnt find anythign to fix the problem. any suggestion?

:confused:

---

### Post by clparker on 2005-10-15
I hate suggesting this, but if you reinstall ubuntu, it may come back, i know its never fun, i've reinstalled ubuntu more times than i can count. It could save you more stress in the long run to get a clean install in.

---

### Post by Qrk on 2005-10-15
I'd try deleting it's entry in /etc/fstab, and then rebooting (I think just restarting x will work, but I'm not sure) then add it back in again. I did that when as similar problem happend to me.

---

### Post by mlomker on 2005-10-15
You'll want to post some more information along with the commands/errors from the terminal when you try to mount it.

```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by aysiu on 2005-10-15
Does it show up as /dev/sdb1 or something like that when you type this in a terminal? ```
sudo fdisk -l
```

---

### Post by S70P on 2005-10-15
Ah thank you everyone i used the ```
sudo fdisk -l
cat /etc/fstab
``` and foudn that sda2 was my other HDD and i just unmounted it and remounted it after i deleted the entry in my /etc/fstab file and it worked perfect

thanks alot!:D :D

---


---
title: "macbook without refit"
date: 2009-08-05
forum: Apple Hardware Users
---

### Post by nTia89 on 2009-08-05
hi to all,

i want to install ubuntu on my MacBook (2,1) without rEFIt but only with GRUB (or grub2) like boot manager.

what can i do ???

PS: i've format my HD and now i have not any partition

---

### Post by nTia89 on 2009-08-05
well i've create a /boot partition flagged as BOOT
and here i've installed GRUB 0.97 and works except one thing

when i power on my macbook i must press ALT and choice manually the HD if not doesn't load !!!!

what can i do ???

to saying to macbook to boot with this partition ?

PS i must have an EFI hd or can i use also MBR . is this the problem ??

---

### Post by cesarse on 2009-08-06
It's normal wait 20 ~ 30 seconds when you're using a pure MBR partition on a Mac. You should not have to hold any key to boot it.

---

### Post by nTia89 on 2009-08-06
then if i change MBR to GPT it boot immediately ???

---

### Post by cesarse on 2009-08-11
It's not so easy.

Sorry if I'm late, but you should read [this post]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21").

---

### Post by rifak on 2009-08-12
> **cesarse said:**
> It's not so easy.

Sorry if I'm late, but you should read [this post]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21").

yeah, i can confirm that this method works

---

### Post by nTia89 on 2009-08-12
> **cesarse said:**
> It's not so easy.

Sorry if I'm late, but you should read [this post]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21").

PERFECT is what i want !!!!!

i've some questions:

1)  the partition table of HD is MBR or GPT ???
2)  what version of GRUB we need ???

thanks

---


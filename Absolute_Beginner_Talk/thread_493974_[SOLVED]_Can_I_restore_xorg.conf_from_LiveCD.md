---
title: "[SOLVED] Can I restore xorg.conf from LiveCD?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-06
I made the mistake in not backing up my default xorg.conf. I tried installing a video driver using ENVY and my video crashed. I am unable to go into Feisty Fawn. Is there a way to restore the default xorg.conf using the LiveCD?
Thanks for your help.
kh

---

### Post by Cypher on 2007-07-06
Boot into Recovery Mode from the GRUB menu and type
```

sudo dpkg-reconfigure -phigh xserver

```

This will allow you to get a nice xorg.conf file..

---

### Post by kittyhawk63 on 2007-07-06
> **Cypher said:**
> Boot into Recovery Mode from the GRUB menu and type
```

sudo dpkg-reconfigure -phigh xserver

```This will allow you to get a nice xorg.conf file..

Wow! You ought to be a NASCAR driver. Such speed.
Thanks.
kh

---

### Post by Nekiruhs on 2007-07-06
I'm uncertain but you might just be able to copy the live CDs xorg.conf to replace yours. Or you could edit the Xorg.conf by hand from the live cd, safe mode, or ttys 1-6. You could also run ```
sudo dpkg-reconfigure -phigh xorg-xserver
```
I think thats the code to reconfigure it.
EDIT: Lol, too late again...

---

### Post by Cypher on 2007-07-06
Oh sorry..'xorg-xserver' is the right package name, I was trying to go from memory..:)

---

### Post by Nekiruhs on 2007-07-06
Lol I had it right then...

---

### Post by kittyhawk63 on 2007-07-06
Thanks people. I could not get the xserver to work as you first gave it, So, I reinstalled Feisty Fawn. Now I see that xorg should have preceded xserver. I will note that for later use if necessary. Thanks again. ;)
kh

---


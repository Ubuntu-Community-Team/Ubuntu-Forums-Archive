---
title: "How to remove Kubuntu"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by opensourcerocks on 2006-02-26
I have just tried to install Kubuntu 64 on my computer, a few times. I does not seem to want to work. How can I remove Kubuntu and grub from the MBP safley with out screwing up windows XP home. 

I will just wait untill Drapper comes out and try it.

---

### Post by Kurt` on 2006-02-26
Well, booted into Windows, you can simply type:

```
fdisk /mbr
```

Into the dos prompt. That will rewrite the master boot record and erase any trace of GRUB.

---

### Post by curtis on 2006-02-26
[QUOTE=Kurt`]Well, booted into Windows, you can simply type:

```
fdisk /mbr
```

Into the dos prompt. That will rewrite the master boot record and erase any trace of GRUB.[/QUOTE]

Actually you need to put in the installation/rescue disc for Windows XP.
Then go into recovery console and type 'fixmbr'

---

### Post by opensourcerocks on 2006-02-26
Thanks You
I will try this if I can't get Drapper to work

---


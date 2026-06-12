---
title: "DEB Files"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2006-06-23
I have got some *deb files for some softwares, Wat do i do wid them. How do i install softwares frm it.

---

### Post by Apple 101 on 2006-06-23
Double-click the Debian package files to install them.

---

### Post by araz on 2006-06-23
[QUOTE=infin?ty]I have got some *deb files for some softwares, Wat do i do wid them. How do i install softwares frm it.[/QUOTE]

use this command:
> [sudo] dpkg -i *.deb

---

### Post by Perfect Storm on 2006-06-23
If you're using Ubuntu Dapper 6.06, just double click.

Ubuntu Breeze and privious version of Ubuntu you need to:

```
cd /where/the/package/is
sudo dpkg -i XXXXXXXXXXXXXX.deb
```

---

### Post by infin?ty on 2006-06-23
Actually i have got xmms player in a *.deb pckg, so i did wht u guys told me. But wat after tht command wat m i supoosed to do next.

After typing tht command i think only the codecs got installed and not the whole player.

---

### Post by bruce89 on 2006-06-23
You can install software from synaptic, see [http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

---

### Post by lapsey on 2006-06-23
just want to clear up any possible confusion: you can install xmms via synaptic or applications > add/remove

codecs are a separate issue - i would be surprised to find a deb for xmms that included codecs. 

if you need codecs, i can reccommend 'easyubuntu' or 'automatix' which are scripts that will help you install what you need.

---

### Post by bruce89 on 2006-06-23
[QUOTE=lapsey]if you need codecs, i can reccommend 'easyubuntu' or 'automatix' which are scripts that will help you install what you need.[/QUOTE]
Or go here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

---


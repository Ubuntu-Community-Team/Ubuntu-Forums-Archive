---
title: "grub issue"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-04-29
i am running two hard drives and currently have windows and ubuntu installed. i'm wanting to get rid of ubuntu on this machine and just have windows. i'll be putting ubuntu on a linux-only machine. right now windows and ubuntu are on different hard drives.

if i were to format the hard drive with ubuntu and create a ntfs partition, wouldn't grub cause conflicts? or would i be fine that way?

thanks for your help!

---

### Post by Kishore Sundara-Rajan on 2006-04-29
May be this thread would be of some help to you:
[http://help.ubuntu.com/starterguide/C/ch05.html]("http://help.ubuntu.com/starterguide/C/ch05.html")

Alternatively, you can modify the GRUB list file:
```

sudo gedit /boot/grub/menu.lst
```

I am a newbie to Ubuntu, so please take my suggestions with a grain of salt.

---


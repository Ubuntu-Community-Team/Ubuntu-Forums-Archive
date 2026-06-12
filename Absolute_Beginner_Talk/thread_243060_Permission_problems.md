---
title: "Permission problems"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by BigManJoe on 2006-08-24
I've been trying to get my iPod to work on here for days. Everytime I try to access it, I get an error saying it's read only. When I try to change the permissions, it says I can't change it because it's read only.

I'm completely new to Linux, so I was wondering if I had to be on the root account to access it? Right now I'm on my joe account and there are lots of things I don't have permission for.

I don't know the root password though because I never set it, so if someone could help me out, tha'd be awsome.

All my apps can read my iPod and I can play music from it, and I could backup my songs in file manager, but when I try to sync, I always get errors like, "Cound not connect to /iPod_Control/iTunes/iTunes DB. Read only."

It's really making me mad because people say it's so easy to access your iPod in Linux and I'm following all the tutorials and nothing is working.

---

### Post by Ziox on 2006-08-24
> **BigManJoe said:**
> I've been trying to get my iPod to work on here for days. Everytime I try to access it, I get an error saying it's read only. When I try to change the permissions, it says I can't change it because it's read only.

I'm completely new to Linux, so I was wondering if I had to be on the root account to access it? Right now I'm on my joe account and there are lots of things I don't have permission for.

I don't know the root password though because I never set it, so if someone could help me out, tha'd be awsome.

All my apps can read my iPod and I can play music from it, and I could backup my songs in file manager, but when I try to sync, I always get errors like, "Cound not connect to /iPod_Control/iTunes/iTunes DB. Read only."

It's really making me mad because people say it's so easy to access your iPod in Linux and I'm following all the tutorials and nothing is working.

to have root permissions...use "sudo" with any command that you would like...

say you are using nautilus as the file manager, then use this command to have root permission for nautilus:

```
gksudo nautilus
```

it'll prompt you for YOUR password...

---

### Post by tzulberti on 2006-08-24
If you haven't change the root password, then it means that there isn't any. For using commands as root, write sudo commando. for example: sudo apt-get update

---

### Post by BigManJoe on 2006-08-24
OK, well, that way I can access it without permissions, but how could I get gtkPod to work with it? Everytime I get a read only error.

---

### Post by trstn on 2008-01-25
> **BigManJoe said:**
> OK, well, that way I can access it without permissions, but how could I get gtkPod to work with it? Everytime I get a read only error.

Hi Joe, i've two ipods - one mounts no problem but the second has the same problem you describe. I also can't change permissions for it, however....

If i launch amarok from a terminal as root ('sudo amarok') it works perfectly, the same for gtkpod, just "sudo gtkpod" in a terminal and you should be right. Hope this helps :)

---


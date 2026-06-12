---
title: "Won’t boot-too many levels of symbolic links"
date: 2019-07-22
forum: Any Other OS
---

### Post by rellyjelly on 2019-07-22
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]So, I was messing with LFS and I needed to have /bin/sh linked to /bin/bash but it was linked to /bin/dash. So I tried to change the link, I used the terminal, but I can’t remember what exactly the command was. I restarted my computer and when I did, It wouldn’t reboot. I get a failed message saying too many levels of symbolic links. I don’t know what to do.[/FONT]

---

### Post by TheFu on 2019-07-22
Boot from some live-boot media and fix it.

---

### Post by rellyjelly on 2019-07-23
And how do I go about fixing this?

---

### Post by rellyjelly on 2019-07-23
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Update: I got onto another Linux os from a different hardrive. I mounted the other drive but when I try to chroot into it, I get this message &#8220;chroot: failed to run command &#8216;/bin/bash&#8217;: Too many levels of symbolic links&#8221;[/FONT]
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]
[/FONT]
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Now what?[/FONT]

---

### Post by Bashing-om on 2019-07-23
rellyjelly; Hummm -- maybe ----

 Maybe we can do this with a simpler mount.

From that alternate OS let's identify the target:
```

sudo fdisk -lu

```
from here we set a mountpoint and mount the target partition and have a look at what is set for the bash path.


[INDENT][INDENT]we can sure try
[/INDENT][/INDENT]

---

### Post by coffeecat on 2019-07-23
Linux from Scratch

*Thread moved to **Any Other OS**.*

---

### Post by TheFu on 2019-07-23
I suspect you deleted the real file and have symbolic links, pointing at symbolic links, pointing at symbolic links.
At some point, the symlink needs to point at a real file.

---

### Post by rellyjelly on 2019-07-23
Why did my post get moved to any other os? The problem is in ubuntu.

---

### Post by rellyjelly on 2019-07-23
How do I fix the symlink to symlink? I only have access to the other OS.

---

### Post by Bashing-om on 2019-07-23
rellyjelly; hey -

> **rellyjelly said:**
> How do I fix the symlink to symlink? I only have access to the other OS.

As in my post #5, mount that target partition and have a look at what is present.

[INDENT]we can do that
[/INDENT]

---

### Post by #&amp;thj^% on 2019-07-23
> **Bashing-om said:**
> rellyjelly; hey -



As in my post #5, mount that target partition and have a look at what is present.

[INDENT]we can do that
[/INDENT]
+1 :)
@rellyjelly>>This my friend will be the most challenging (Hopefully lesson learned) feat you will ever do on linux system, my advice is to back-up what you can and re-install the system.
Fixing this will involve at least reinstalling the packages which provide the missing symlinks...

If you create your symlink like this:
**_Example only!_**
```

cd /usr/local/etc
ln -s nginx/ /etc/nginx
```

You will in fact make the link /etc/nginx -> /etc/nginx, because the source path is relative to the link's path. The solution is as simple as using absolute paths:
**_Example only!_**
```

ln -s /usr/local/etc/nginx /etc/nginx
```

I like using find's -L option combined with the -type l test allows broken symlinks to be identified; then dpkg -S will identify the corresponding package in most cases:
[/code]
```
dpkg -S $(find -L /usr/bin -type l)
```
Or:
```
cd /suspected/directory
find -L ./ -mindepth 15

```
Filtering this and feeding it to apt-get allows the packages to be reinstalled:
```

apt --reinstall install $(dpkg -S $(find -L /usr/bin -type l) | grep -v "diversion by" | cut -d: -f1)
```
I've only done this once years ago, and I won't do it again. (It took ages to fix and re-fix)

---


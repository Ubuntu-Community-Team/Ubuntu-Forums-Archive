---
title: "I just added an IDE HD w/Mac OS 9. How to configure yaboot?"
date: 2008-06-03
forum: Apple Hardware Users
---

### Post by Alaska_Jack on 2008-06-03
Hi all, TOTAL newbie here. Here's what I've got:

Blue & White G3
Xubuntu 7 installed on IDE Hard Drive (Master)

Separate HD with Mac OS 9 installed on IDE bus as slave

Xubuntu can mount OS 9 disk fine.

I would like to be able to boot to the OS 9 disk as well. But yaboot doesn't give me that option on startup. I've struggled through a lot of research on this, and I know there is a yaboot config file somewhere. But can someone explain to me in simple terms what I need to put in this file?

I promise I'll learn from this!

  - Alaska Jack

---

### Post by hpp3 on 2008-06-03
Your yaboot configuration file is /etc/yaboot.conf.
To edit it in Xubuntu type
```

gksudo mousepad /etc/yaboot/conf

```
and put a line in there that says:
```

macos=/dev/hda2

``` 
save it, and run 'sudo ybin' in a terminal to finalize your changes and reboot.
If that throws an error or doesn't work, replace **h**da2 with **s**da2, save and run ybin.

If it worked, at the yaboot prompt, you should be able to press M to boot into your mac system.

Hope this helps...

---


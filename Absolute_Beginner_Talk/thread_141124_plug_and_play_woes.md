---
title: "plug and play woes"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by spencewah on 2006-03-07
Kubuntu won't recognize my SanDisk usb drive when I plug it in, instead I get a big error in Konquerer:



> An error occurred while loading media:/sdb1:

The file or folder media:/sdb1 does not exist.

This pops up twice.  Any ideas? :-k

---

### Post by aysiu on 2006-03-07
That bug was around way back when...

[http://kubuntuforums.net/forums/index.php?topic=266.msg3000#msg3000](http://kubuntuforums.net/forums/index.php?topic=266.msg3000#msg3000)
[http://kubuntuforums.net/forums/index.php?topic=524.0](http://kubuntuforums.net/forums/index.php?topic=524.0)

I even filed a bug report on it in October.

I believe it's been fixed, as I have a Sandisk player and no longer experience that problem.

Try just updating: KMenu > System > Konsole ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---


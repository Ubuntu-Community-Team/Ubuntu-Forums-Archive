---
title: "remove by force"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-11-20
how can i remove by force a locked file that i dnt have permission to remove even when in root, because i installed realplayer in the wrong place and it;s not working with the shortcut in applications, and i instaled a java thingy on my desktop too and i want to remove that too,
thanks

---

### Post by aysiu on 2006-11-20
Root should be able to delete anything.

Can you *cd* to the folder and post the output here of this command? ```
ls -al
```

---

### Post by Mazen on 2006-11-20
> **aysiu said:**
> Root should be able to delete anything.

Can you *cd* to the folder and post the output here of this command? ```
ls -al
```

mazen@mazen-laptop:~/Desktop/Programs$ cd RealPlayer/
mazen@mazen-laptop:~/Desktop/Programs/RealPlayer$ ls -al
total 660
drwxr-sr-x 11 root  root    4096 2006-11-15 05:58 .
drwxr-xr-x  3 mazen mazen   4096 2006-11-18 00:32 ..
drwxr-sr-x  2 root  root    4096 2006-11-15 05:58 Bin
drwxr-sr-x  2 root  root    4096 2006-07-19 00:17 codecs
drwxr-sr-x  2 root  root    4096 2006-07-19 00:17 common
drwxr-sr-x  2 root  root    4096 2006-07-19 00:17 doc
-rw-r--r--  1 root  root   25667 2006-11-15 05:58 install.log
drwxr-sr-x  2 root  root    4096 2006-07-19 00:17 lib
-rwxr-xr-x  1 root  root   11286 2006-07-19 00:17 LICENSE
drwxr-sr-x  2 root  root    4096 2006-07-19 00:17 mozilla
drwxr-sr-x  2 root  root    4096 2006-07-19 00:17 plugins
drwxr-sr-x  2 root  root    4096 2006-07-19 00:17 postinst
-rw-r--r--  1 root  root    3047 2006-07-19 00:17 README
-rwxr-xr-x  1 root  root    2499 2006-11-15 05:58 realplay
-rwxr-xr-x  1 root  root    2486 2006-11-15 05:58 realplay.bak
-rwxr-xr-x  1 root  root  570344 2006-07-19 00:17 realplay.bin
drwxr-sr-x  7 root  root    4096 2006-07-19 00:17 share
 this is what i got

---

### Post by aysiu on 2006-11-20
So which of those files are you trying to remove?

---

### Post by Mazen on 2006-11-21
> **aysiu said:**
> So which of those files are you trying to remove?

All of them including the one that contains them!

---

### Post by hyper_ch on 2006-11-21
Do first:

cd ~/Desktop/Programs


then:

sudo rm -Rf RealPlayer

---


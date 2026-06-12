---
title: "problem accessing folders through temrinal"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by Matt Houston on 2005-12-03
```
adrian@Adrian:~$ ls -ls
total 906852
     4 drwxr-xr-x   3 adrian adrian      4096 2005-12-03 02:13 Desktop
     4 drwxr-xr-x   5 adrian adrian      4096 2005-11-27 10:49 Downloads
264880 -rw-r--r--   1 adrian adrian 270965248 2005-12-03 04:54 et-linux-2.60.x86.run
   336 -rw-r--r--   1 adrian adrian    336383 2005-11-23 19:53 Firefox_wallpaper.png
     4 drwxrwxrwx  27 adrian adrian      4096 2005-12-03 01:50 Music
     4 drwxrwxrwx   6 adrian adrian      4096 2005-11-26 16:24 Pictures
  1072 -rw-r--r--   1 adrian adrian   1091525 2005-11-26 15:41 pulman_totw.mov
     4 drwxrwxrwx   4 adrian adrian      4096 2005-12-03 12:39 Stuff
640536 -rw-r--r--   1 adrian adrian 655259648 2005-11-15 20:46 ubuntu-5.04-live-i386.iso
     4 drwxrwxrwx   4 adrian adrian      4096 2005-11-11 19:11 Video
     4 drwxr-xr--   2 root   root        4096 2005-11-16 20:25 Windows
adrian@Adrian:~$ cd stuff
bash: cd: stuff: No such file or directory
adrian@Adrian:~$ cd video
bash: cd: video: No such file or directory
adrian@Adrian:~$ cd music
bash: cd: music: No such file or directory
adrian@Adrian:~$

```

Any ideas why?

---

### Post by 23meg on 2005-12-03
File and directory names are case sensitive.

---


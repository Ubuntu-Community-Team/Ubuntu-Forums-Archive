---
title: "[SOLVED] folders locked"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by l337a on 2007-09-27
It was probably stupid to run wget under sudo. (Im currently attempting to save all jpeg files from the site, but with no avil)

Now I have a bunch of locked folders in my home directory. I can't delete them, even under root.

tyler@tyler-desktop:~$ sudo rm '/home/tyler/e-hentai.org' 
rm: cannot remove `/home/tyler/e-hentai.org': Is a directory
tyler@tyler-desktop:~$ 

That's what I get. And Yes, hentai.  The situation is odd, but the problem is genuine.

---

### Post by swisscow on 2007-09-27
try

```
sudo rm -rf folder/
```

---

### Post by l337a on 2007-09-27
It removed a good chunk of everything, thank god. But theres still some files that REFUSE to leave!

---

### Post by swisscow on 2007-09-28
Well it's a start. Right click on one of the files that's refusing to go and have a look at the permissions, owner, group etc. Post them, maybe it is something to do with that.

---


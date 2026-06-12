---
title: "Combining Two Cd's into One .iso"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-04-09
I am looking for a way to take two install cds for a windows game, and combine them into one install DVD so that I can run the installer in wine without using a loki installer (which has not been working for me). I know that it is possible to use the dd command in terminal to copy one cd to .iso (even though I don't exactly understand how to do it), but is it possible to do the same thing with two cds to one .iso?? Any help would be greatly appreciated!!

---

### Post by terdon on 2007-04-09
you could just mount both isos and then make a new iso from both directories```

mount -t iso9660 -o loop iso1 dir1
mount -t iso9660 -o loop iso2 dir2
mkisofs -R -J -L -l -o 2cd.iso dir1 dir 2

```

Or, you could sequentally copy the cd's contents into one directory and then use whatever you use to burn cds to make a cd out of them.

Finally you could try to cat the 2 isos into one file (but I don't think this will work):```

cat iso1 iso2 > 2cds.iso
```

---

### Post by kpkeerthi on 2007-04-09
Try [ISOMaster]("http://www.getdeb.net/comment.php?rel_id=550")

---


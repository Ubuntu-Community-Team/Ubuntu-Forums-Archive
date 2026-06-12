---
title: "problems updating to 7.10"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by NeoEIRE on 2008-04-15
when i click update in the "Update Manager"

i get this error:
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)

any ideas?
plus if i want to duel boot with Win XP 64bit when i have(at the moment 7.04),
how do i do this? or do i have to start again fresh???

thanks

---

### Post by OffAxis on 2008-04-15
edit your /etc/apt/sources.list file.
```
sudo nano /etc/apt/sources.list
```

and comment out the lines that have **medibuntu **or **wine.lowvoice.nl** in them by putting a **#** sign at the beginning of them. There's a few examples in there; just stick to the same formatting.
After you're done adding the #s then 
**CTRL+X** (to exit), 
**Y** (Yes Save Changes)
 **Enter **(to save with the same name; sources.list)
 and 
```
sudo apt-get update
```

and then you can run your system upgrade.

---


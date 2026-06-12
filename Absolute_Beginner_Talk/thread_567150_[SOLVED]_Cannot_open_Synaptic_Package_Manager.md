---
title: "[SOLVED] Cannot open Synaptic Package Manager"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Yorkshire Lad on 2007-10-04
Hi ,

A complete newby to Linux so please go easy .

I am running Ubuntu Feisty Fawn .

Yesterday I tried to download and install Virtualbox  but the install failed due no doubt to my inexperiance. Now when trying to open Synaptic I get the following error.

 E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have tried searching the forums and applied the suggestions in the 6 threads I found but nothing works. sudo synaptic gives the same results.

Any ideas how to fix this.

Cheers
Rick

---

### Post by bapoumba on 2007-10-04
Please open a terminal (Accessories > Terminal), and run :
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by Yorkshire Lad on 2007-10-04
Thanks matey.!

Just found that info by googling at [https://answers.launchpad.net/ubuntu/+source/gdebi/+question/7135]("https://answers.launchpad.net/ubuntu/+source/gdebi/+question/7135")

So did it while you were posting, many thanks all thesame for the quick reply .

Rick

---

### Post by n3tfury on 2007-10-04
plz marked solved

---

### Post by bapoumba on 2007-10-04
> **n3tfury said:**
> plz marked solved
kk, dunnit ^^

---


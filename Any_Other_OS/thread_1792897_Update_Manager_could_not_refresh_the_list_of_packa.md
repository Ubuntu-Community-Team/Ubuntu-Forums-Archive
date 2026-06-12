---
title: "Update Manager could not refresh the list of packages"
date: 2011-06-28
forum: Any Other OS
---

### Post by Candlehawk on 2011-06-28
I'm not sure this is the correct place to put this, but it seemed to have made the most sense.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.linuxmint.com_dists_katya_import_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Running Mint 11.04, but I have had nothing but bad experience with Mint forums.

---

### Post by dr.abady on 2011-06-28
im having the same problem > this message appears
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Perfect Storm on 2011-06-29
Moved to Other OS/Distro Talk.

---

### Post by Rubi1200 on 2011-06-29
Hi and welcome to the forums Candlehawk and dr.abady :)

Caveat: the fix I will suggest works for Ubuntu but I am not 100% sure about Linux Mint (in theory it should be fine since it is based on Ubuntu).

Open a terminal and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by Candlehawk on 2011-06-29
Thank you so much. Sorry about putting the header wrong on the post, and not knowing where to put it. Thanks, and: Solved.

---

### Post by Rubi1200 on 2011-06-29
Excellent! I am really pleased you got this sorted out :-)

You can also mark this Solved using the Thread Tools near the top of the page.

---


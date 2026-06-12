---
title: "How to find a system file??"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by thunderbard on 2007-08-29
When I try to use File Browser it only seems to find files that are in the "username" category.  Even when I look for files or folders that I _know _exist because I see them in the File Browser window, the search function comes up short.

In particular, I'm looking for "conf-cc". It should be part of a qmail installer but it needs to be altered because the Ubuntu 6.06 version of glibc is newer than 2.3.1...according to the recently released "Qmail Quickstarter" book.

wassup?

---

### Post by enderwig on 2007-08-29
```
cd / 
sudo find -name *conf-cc*
```

---

### Post by gundumfx on 2007-08-29
cd / 
sudo find -name *conf-cc*

---

### Post by thunderbard on 2007-08-29
...I was hoping for a GUI solution...:(

thanks anyway!:)

---

### Post by diatribe on 2007-08-29
catfish is a gui frontend to several commandline file locators

---

### Post by thunderbard on 2007-08-29
Ok...I tried:

cd /
sudo find -name *conf-cc*

and got the foillowing return:

WARNING: Hard link count is wrong for ./proc/4792: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

:confused:

---


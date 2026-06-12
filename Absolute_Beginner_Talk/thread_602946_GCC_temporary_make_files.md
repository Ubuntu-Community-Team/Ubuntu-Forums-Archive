---
title: "GCC temporary make files?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by bethebunny on 2007-11-04
Using the latest stable Debian;

I was recently trying to install cvswine to run some games; however, the make had taken almost an  hour already and the kernel was yelling at me every few seconds because my processor was over its heat threshold, so I killed the make. Now, I can't find the files anywhere in the filesystem (none of the folders show sizes over a few dozen megs) but I have 1 gig less available space on my hard drive. Where might these temporary make files be, and how might I get rid of them?

---

### Post by HermanAB on 2007-11-04
Hmm, you likely need to reboot and run fsck to fix the file system.

Cheers,

Herman

---

### Post by Kymus on 2007-11-04
If I am understanding you correctly, I had a similar problem with GCC and **make**. It took foreeeeeeeeeeeever to compile and in the end, it just spit some confusing error at me.

To get rid of the temporary files, try **make clean**

---

### Post by bethebunny on 2007-11-04
fsck simply said: /dev/hdb1: clean, 133078.498976 files, 853791/996022 blocks

"make clean" and "make clean /dev/hdb1" resulted in "makeL *** No rule to make target 'clean'. Stop."

Any other ideas? Or an idea of how to get either of these to work as you intended?

---


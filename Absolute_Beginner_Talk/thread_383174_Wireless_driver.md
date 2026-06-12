---
title: "Wireless driver"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by pesach on 2007-03-12
I am trying to install a wirell driver, and it tells me to
 Copy these
files to /lib/firmware/zd1211, where it can be loaded by the
rewritten zd1211 driver.
How do I do this?
(please answer this as if talking to someone who had never heard of ubuntu before. the only I know how to do is open terminal).
Thanks!

---

### Post by chuckyp on 2007-03-13
Open a terminal and cd to the directory where the files are that you want to copy.   Then type in sudo cp <nameoffiles> /lib/firmware/zd1211

You may be able to drag and drop the files by starting nautilus as root.  To do this open a terminal and gksu nautilus.   This will open a file browser window you should just be able to drag and drop the files to the /lib/firmware/zd1211 directory in that window.

Also I beleive the firmware you are trying to copy over has to go in /lib/firmware/'kernel version'/zd1211   So you might want to read the instructions once again.

---

### Post by pesach on 2007-03-13
> **chuckyp said:**
> Open a terminal and cd to the directory where the files are that you want to copy.   Then type in sudo cp <nameoffiles> /lib/firmware/zd1211
I hate to sound like a noob, but what does this mean?
more specifically, what does "cd" mean, and the directory you speak of is lib/frimware/zd1211?
Rememebr, I KNOW NOTHING.

---

### Post by mi_were on 2007-03-13
> **pesach said:**
> I hate to sound like a noob, but what does this mean?
more specifically, what does "cd" mean, and the directory you speak of is lib/frimware/zd1211?
Rememebr, I KNOW NOTHING.

"cd" mean change directory literally and it is the command to use at the terminal.

---

### Post by pesach on 2007-03-14
So I didi that, copied in the files then what do I do? I clicked on on eand this came up
Cannot open /lib/firmware/2.6.17-11-generic/zd1211/zd1211b_ub: No application suitable for automatic installation is available for handling this kind of file
what shoud I do know?

---


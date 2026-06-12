---
title: "Can't get past DVD encryption..."
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2005-12-20
I got the css thing, but when I try to run it in the terminal, this is what I get:

[b]~$ sudo dpkg -i libdvdcss2_1.2.8-1unofficialubuntu3_i386. deb
dpkg: error processing libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb[/b]

Does the file need to be somewhere specific?

---

### Post by aysiu on 2005-12-20
If the file's on your desktop, you need to do this: ```
cd Desktop
sudo dpkg -i libdvdcss2_1.2.8-1unofficialubuntu3_i386. deb
```

---

### Post by SZF2001 on 2005-12-20
Wow... It's playing the Best of Chris Farley... YESSS

But... It's all choppy. Is there a way to fix that?

---

### Post by invalid on 2005-12-20
Make sure you have DMA enabled for your dvd drive:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447)

---


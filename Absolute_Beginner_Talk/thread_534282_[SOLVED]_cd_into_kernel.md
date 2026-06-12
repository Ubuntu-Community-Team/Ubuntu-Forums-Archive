---
title: "[SOLVED] cd into kernel"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-25
Hi Ubuntu community,

I am assisting another user in an installation, but had a quick question as to how to instlling a kernel source.

These are the url's directions:
> 
You also need to install the kernel source corresponding to the kernel on your system (most distros come with a kernel source package). Go into the kernel subdirectory of the package

this is his thread:   [http://ubuntuforums.org/showthread.php?t=534250](http://ubuntuforums.org/showthread.php?t=534250)
this is the url:  [http://www.amxl.com/option,com_content/task,view/id,1/Itemid,1/](http://www.amxl.com/option,com_content/task,view/id,1/Itemid,1/)

anyone care to assist, jump on in, the waters timid.

---

### Post by ddrichardson on 2007-08-25
```
uname -r
``` gives the kernel name. Once the kernel source is installed along with all the other stuff it needs it's stored in /usr/src/linux - usually by version number.

Its a very poorly worded guide, aimed at people who know what they are doing. Essentially you are building and inserting a kernel module as a different driver for the card.

As I stated on the other post - this is illegal in the UK - by virtue of the Wireless Telegraphy (2007) Act.

---


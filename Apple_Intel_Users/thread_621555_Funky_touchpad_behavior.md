---
title: "Funky touchpad behavior"
date: 2007-11-23
forum: Apple Intel Users
---

### Post by umneydurak on 2007-11-23
Ok, so I pretty much setup my mac the way I like, wireless works, suspend works, compiz works. Even mapped right click to keyboard "enter" key. Only thing is my touchpad behaves really funky when I try to drag or scroll with it. i.e. Holding down a "mouse" button while moving cursor with touchpad. Cursor either unresponsive, or just stops moving. Not sure if I am clear. Sorry. :(
Anyway anyone know how to fix this?

Thanks.

---

### Post by Grey Box on 2007-11-27
This is covered in other threads and a pretty good [howto]("https://help.ubuntu.com/community/MacBook"), but to cut a long story short, there is a lot of adjusting and so forth you can do with modifications to xorg.conf or using a synaptics frontend, but the jumpy trackpad cursor on macbooks is due to bugs in the driver that is in current ubuntu (and other distro) kernels. 

I have seen a patch around to correct this problem and bring the sensitivity of two finger scrolling and so forth to almost as good as OS X, but I haven't done this myself (it isn't pissing me off enough yet!).

---


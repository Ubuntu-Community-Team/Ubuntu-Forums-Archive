---
title: "Advice on way to install driver, is what I need"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Mortimer on 2006-01-21
I have a trablet that I want to run on ubuntu, there is a driver for it, but I'm not sure how to install it. The latest version, which is [on this page](http://linuxwacom.sourceforge.net/) says it needs a newer linux kernel than what breezy badger uses. I'm not sure even if this is what I should do, or will it break other drivers.
I'm thinking it might be better to compile the driver for 2.6.12-9-386 ? I'm not sure. Anything useful that someone can tell me about it is appreciated.

---

### Post by ysse on 2006-01-21
The linuxwacom page says that version 0.7.2 *supports* kernel version 2.6.13/14, not that it's required.

On the help page, it says kernel 2.4.20 and up, so I don't think it sounds hopeless.

---

### Post by ubuntuuser on 2006-01-21
[QUOTE=Mortimer]I have a trablet that I want to run on ubuntu, there is a driver for it, but I'm not sure how to install it. The latest version, which is [on this page](http://linuxwacom.sourceforge.net/) says it needs a newer linux kernel than what breezy badger uses. I'm not sure even if this is what I should do, or will it break other drivers.
I'm thinking it might be better to compile the driver for 2.6.12-9-386 ? I'm not sure. Anything useful that someone can tell me about it is appreciated.[/QUOTE]
You will need to install build-essential and the kernel-headers before you can compile it. I quickly checked the documentation provided on that website and it seems to be quite good. Just follow it step by step and you should be fine. If not, post further questions and include any error messages you might get.

---


---
title: "driver for d-link dwl-g122?"
date: 2006-07-05
forum: Apple PPC Users
---

### Post by erez1012 on 2006-07-05
hii i buy the dwl-g122 usb  and i want to use this usb in my ubuntu!!
ubuntu have adriver for that usb?? 
what software i need for this d-link??

i have a ibook g3 300mhz 200 ram
thanks:)

---

### Post by jISh on 2006-07-05
See my link [here]("http://www.ubuntuforums.org/showthread.php?t=209315&highlight=dwl-g122")

It was intended for PC users, maybe it will work for you, too. If it does, please let me know.

---

### Post by erez1012 on 2006-07-05
ok/
tha:)nks

---

### Post by dkitty on 2006-07-24
ndiswrapper won't work on PowerPC processors. To quote a few peeps from [this thread](http://www.ubuntuforums.org/archive/index.php/t-190248.html):

> ndiswrapper can't works on ppc since it use x86 binary dll. It could compile but dll can't be used.

> We're talking about the reason there is a separate PPC version of anything in the first place, the processor architecture is entirely different and anything compiled into machine code for a x86 system will not run on such a cpu natively, period.

ndiswrapper works like a charm when using the dwl-g122 usb dongle (rev b, I think) on an old P2 desktop I have. I can't use ndiswrapper for my PowerPC iBook though.

---


---
title: "ubuntu minimal and tty problem"
date: 2012-05-12
forum: Apple Hardware Users
---

### Post by amusis on 2012-05-12
I have ubuntu minimal and i login without problem , but when i start fluxbox(with startx) i can not returner in tty shell because this is what i see

[http://imageshack.us/photo/my-images/851/imageozl.jpg/](http://imageshack.us/photo/my-images/851/imageozl.jpg/)

I don't know where problem is, so can you help me?

Sorry for the quality of this picture.

tnx

---

### Post by amusis on 2012-05-18
some one ? help? no? no idea?

---

### Post by papibe on 2012-05-18
Hi amusis.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the link here.

Regards.

---

### Post by amusis on 2012-05-19
ok here the link

[http://paste.ubuntu.com/996557/](http://paste.ubuntu.com/996557/)

i hope it work

thanks

---

### Post by papibe on 2012-05-19
There is an error saying it is not possible to read the Video BIOS, but later the driver is able to get the EDID information just fine.

What is your exact graphic card?
Could you post the result of these commands?
```
lspci -nn | grep -i vga

sudo lshw -C display
```
I noticed that you are using the 'RADEON' open source driver. If your card is not too old, may be the ATI proprietary driver could solve your problem.

Regards.

---

### Post by amusis on 2012-05-20
here the commands you ask me

[http://paste.ubuntu.com/997357/](http://paste.ubuntu.com/997357/)

tnx

---

### Post by papibe on 2012-05-20
I tried to determine if your card is supported by the ATI proprietary driver (fglrx), but I had no luck. My first impression is that is not supported.

At this point, I running out of ideas. Hopefully someone else will pitch in.

Regards.

---

### Post by amusis on 2012-05-21
ok,no problem,  tnx for your help

---


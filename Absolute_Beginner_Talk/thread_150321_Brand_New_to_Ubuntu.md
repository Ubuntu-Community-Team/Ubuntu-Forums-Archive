---
title: "Brand New to Ubuntu"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by typ3 on 2006-03-25
I'm brand new to Ubuntu. In fact I'm brand new to linux in general (expect for an attempt at using Red Hat 6 years ago). 

I've just installed Ubuntu and I'm loving it but I've run into a problem. My graphics card is an old Matrox MGA G200 and it doesn't seem to be supported. I looked in the Device Manager menu and it isn't showing up as working/installed/whatever. 

How do I go about installing and configuring this graphics card?

Thanks in advance,

Brandon

P.S: I'm a Ubuntu forum and Linux newb. Please go easy on me.

---

### Post by dcstar on 2006-03-25
[QUOTE=typ3]I'm brand new to Ubuntu. In fact I'm brand new to linux in general (expect for an attempt at using Red Hat 6 years ago). 

I've just installed Ubuntu and I'm loving it but I've run into a problem. My graphics card is an old Matrox MGA G200 and it doesn't seem to be supported. I looked in the Device Manager menu and it isn't showing up as working/installed/whatever. 

How do I go about installing and configuring this graphics card?

Thanks in advance,

Brandon

P.S: I'm a Ubuntu forum and Linux newb. Please go easy on me.[/QUOTE]
CTRL-ALT-F1
log in with your username and password
```
sudo dpkg-reconfigure xserver-xorg
```
select "Matrox" (if it already wasn't there) and just select the defaults for the rest, then:
```
sudo reboot
```

---


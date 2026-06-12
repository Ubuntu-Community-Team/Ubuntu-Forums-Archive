---
title: "Japanese input in openoffice"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by te.ss on 2007-05-12
Hi,

It's been a few weeks since I finally switched to Ubuntu from XP.  Things are not always as easy as before (due to my lack of knowledge) but I'm glad I made a switch. 

Now, I want to input Japanese texts in an openoffice document and installed SCIM-Arthy. It allowed me to input Japanese when composing mails in Evolution and in text editor but didn't work in openoffice and also, the firefox.  

Can anyone give me some advise / direction?  
I'm using *
 Dapper
 Openoffice 2.0.2
 SCIM-arthy 0.8.0

Thanks

---

### Post by Najand on 2007-05-12
OK. I try to help you to make it.
FIrst:
As far as I don't know you have all packages or not, do this in a terminal:
```
sudo apt-get install uim anthy scim-gtk2-immodule scim-uim scim-tables-ja
```
Then open the scim_startup file:
```
gksudo gedit /etc/X11/Xsession.d/74custom-scim_startup
```
Add these lines:
```
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
```
Now restart X (by pushing Ctrl+Alt+Backspace) and see if it works.

---

### Post by shirilover on 2007-05-13
That works fine to include scim at startup, but to input in OpenOffice, try the following instructions:
[Ubuntu CJK Input Guide]("http://www.mrbass.org/linux/ubuntu/scim/")
scroll down and you should see the OpenOffice screenshots.

---

### Post by te.ss on 2007-05-13
Najand,

I tried your advise and voila!  It worked (even Katakana-Zenkaku key works)!  Now I can type in openoffice and firefox.

Thanks!

---

### Post by te.ss on 2007-05-13
Sirilover

It's a nice guide with actual pictures.  It seems sooner or later I need to learn to use some commands to meet my needs (very small, nothing fancy).  

Thanks

---


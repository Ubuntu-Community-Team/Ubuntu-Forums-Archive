---
title: "Problems installing xmms: GLIB &gt;=1.2.2 not isntalled"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by cocotu on 2006-10-17
If I try to install the source code ./configure fails with this error:

checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

I'm using Ubuntu 5.10, I was thinking about upgrading to 6.10. Right now I don't have Internet access at home I only have the Ubuntu 6.10 CD. How can I install this GLIB thing!?? Does anybody have a clue? Thanks for the help

---

### Post by Old Pink on 2006-10-17
Why not just type the following in a terminal?```
sudo aptitude install xmms
```Easy as pie! :)

**EDIT: **Because you don't have the internet.  ](*,) :-#

---

### Post by TrendyDark on 2006-10-17
> **Matt.H said:**
> Why not just type the following in a terminal?```
sudo aptitude install xmms
```Easy as pie! :)

](*,) He doesn't have internet access.

---

### Post by Old Pink on 2006-10-17
> **TrendyDark said:**
> ](*,) He doesn't have internet access.

Yeah I know, I edited the post. 

Anyway, back to GLIB. Download it on your current PC and install it on your Ubuntu PC? :)

---

### Post by cocotu on 2006-10-17
I'm comfused!! Sorry, can you explain that again, I don't have Internet NOT able to download anything. Only have the CDs for 5.10 and 6.10..Thanks

---

### Post by TrendyDark on 2006-10-17
I think what he means is download the GLIB package onto the PC you're using now, then transport the file to your Ubuntu PC (USB Drive, CD-R, etc) and install the package.

---

### Post by cocotu on 2006-10-17
Ok, I have been looking for tha GLIB package where do I get it??
Thanks

---

### Post by cocotu on 2006-10-19
I download it and install the glib package and still keep getting the same error!! HELP!!

---

### Post by edwinzeng on 2007-12-19
you need to type:
sudo apt-get install libglib1.2-dev

---

### Post by LinuX-M@n1@k on 2008-04-10
> **edwinzeng said:**
> you need to type:
sudo apt-get install libglib1.2-dev

He does NOT have INTERNET CONNECTION !!
Read before you post !

---


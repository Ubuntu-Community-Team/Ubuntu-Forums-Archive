---
title: "configure error"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-10-12
I managed to solve a number of similar errors by using synaptic to find and install the necessary libraries i.e: glib and libxml to name only two.  However I'm at the end of my rope with this one:

Error Message:
```
checking for gtk+-2.0 >= 2.6... no
Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```
 

I'm running Feisty and I'm trying to compile GnuCash-2.2.1 and I'm pretty damn sure I have gtk+-2.0 >= 2.6 on my box already. Right?  Isn't it part of Gnome?  If so where can i find it and where can I change this config_path?

I know I could just be happy with the gnucash I have now but thats not the point.

---

### Post by FuturePilot on 2007-10-12
```
sudo apt-get install libgtk2.0-dev
```
Is what you want.

---

### Post by rsambuca on 2007-10-12
I am not sure how much difference there is, but version 2.02 is in the ubuntu repositories, so you could install that without compiling from source.  Another alternative would be to wait until next week as GnuCash 2.2 is the default version in Gutsy.

---

### Post by Jive Turkey on 2007-10-12
> **rsambuca said:**
> I am not sure how much difference there is, but version 2.02 is in the ubuntu repositories, so you could install that without compiling from source.  Another alternative would be to wait until next week as GnuCash 2.2 is the default version in Gutsy.

Ahh, good to know but I do need to compile it in order to enable the HBCI plugin, at least I did with the previous version.  It has to do with a licencing issue, not a functionality issue I believe, so that option may never be available by default in a deb package.

Thanks for the replies, I'll try that lib when I get home from work tonight.

---

### Post by Jive Turkey on 2007-10-13
yep, that was the one, I still had 2 more before ./configure would finish without errors, but they were easy enough to find.  I saw gnucash-2.2.1 available in addremove today, but I can t tell if that's mine or if its in the repos.  AFAIK one needs to compile it one's self using "./configure --enable-hbci" in order to have the direct access to ofx at a bank.  My bank wont allow web browser downloads of ofx files and they claim you can only use MSmoney or Quicken.  Gnucash is working just fine for me though :)

---


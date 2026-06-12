---
title: "help with getting wireless to work on my macbook"
date: 2007-08-04
forum: Apple Intel Users
---

### Post by mshale on 2007-08-04
Hey everyone!

I have purchased a new macbook.  it's just the regular 13.3 black one... but i'm trying to get the wireless to work.  I'm running ubuntu using VMware fusion... I tried the walkthrough written by benazo... but to no avail.  it still doesn't even recognize that there is a wirless card in here... any more suggestions for me??

---

### Post by mshale on 2007-08-04
ok, so forgive me for pasting, but i have discovered that the wireless works... I use that term a bit loosely, however.  I can browse the internet using wireless... but the network manager says that i'm connected via a wired connection (weird huh?).  that means that i'm evidently connected to a wireless connection, but it's not recognizing it.  when i follow the last step of the walkthrough, i type in iwconfig -find or something (can't remember the exact code) it gives me an error message that says something similar to "device does not support searching"  don't know if that has much do do with anything though.  

But thanks for reading!! lol


P.S. i found an answer [HERE]("http://ubuntuforums.org/showthread.php?t=417240&highlight=kde+desktop")  I'm not sure how i did it, for i didn't mod any settings in VMware fusion.

---

### Post by benanzo on 2007-08-04
VMWare builds a "bridge" device for networking inside a virtual machine.  To my knowledge it just uses Ubuntu's ethernet device (eth0) not the wireless interface (ath0).  So even though you may be connected to wireless in OS X, through OS X's wireless interface, it is just bridged to Ubuntu's ethernet device.  You don't have to do anything with the wireless if you're running Ubuntu in a VM.  That is why Ubuntu thinks it's using ethernet, not wireless, even though you are connected wirelessly.

---

### Post by mshale on 2007-08-04
I know this is very off topic... but i'm having trouble getting the new version of k9copy to work.  ./configure finishes, and make finishes i think... here is some of the output of the terminal.  maybe we need to move this thread... but...
```

av/libk9dvdnav.la ../libk9copy/libk9copy.la ../k9decmpeg/libk9decmpeg.la ../k9vamps/libk9vamps.la ../k9devices/libk9devices.la -lkmdi -lkdeui 
make[3]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2/src'
make[2]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2/src'
Making all in po
make[2]: Entering directory `/home/matt/Desktop/k9copy-1.1.2/po'
rm -f es.gmo; : -o es.gmo ./es.po
test ! -f es.gmo || touch es.gmo
rm -f cs.gmo; : -o cs.gmo ./cs.po
test ! -f cs.gmo || touch cs.gmo
rm -f ru.gmo; : -o ru.gmo ./ru.po
test ! -f ru.gmo || touch ru.gmo
rm -f de.gmo; : -o de.gmo ./de.po
test ! -f de.gmo || touch de.gmo
rm -f ca.gmo; : -o ca.gmo ./ca.po
test ! -f ca.gmo || touch ca.gmo
rm -f pt_BR.gmo; : -o pt_BR.gmo ./pt_BR.po
test ! -f pt_BR.gmo || touch pt_BR.gmo
rm -f fr.gmo; : -o fr.gmo ./fr.po
test ! -f fr.gmo || touch fr.gmo
rm -f pl.gmo; : -o pl.gmo ./pl.po
test ! -f pl.gmo || touch pl.gmo
rm -f es_AR.gmo; : -o es_AR.gmo ./es_AR.po
test ! -f es_AR.gmo || touch es_AR.gmo
rm -f el.gmo; : -o el.gmo ./el.po
test ! -f el.gmo || touch el.gmo
rm -f it.gmo; : -o it.gmo ./it.po
test ! -f it.gmo || touch it.gmo
make[2]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2/po'
Making all in doc
make[2]: Entering directory `/home/matt/Desktop/k9copy-1.1.2/doc'
Making all in k9copy
make[3]: Entering directory `/home/matt/Desktop/k9copy-1.1.2/doc/k9copy'
/usr/bin/meinproc --check --cache index.cache.bz2 ./index.docbook
make[3]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2/doc/k9copy'
make[3]: Entering directory `/home/matt/Desktop/k9copy-1.1.2/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2/doc'
make[2]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2/doc'
make[2]: Entering directory `/home/matt/Desktop/k9copy-1.1.2'
make[2]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2'
make[1]: Leaving directory `/home/matt/Desktop/k9copy-1.1.2'
```


Thanks a ton!

---

### Post by benanzo on 2007-08-04
you're probably missing some dependency(ies).  Check the INSTALL file, and make sure that for all the packages it requires you install the -dev packages from the repos.

---

### Post by mshale on 2007-08-04
> **benanzo said:**
> you're probably missing some dependency(ies).  Check the INSTALL file, and make sure that for all the packages it requires you install the -dev packages from the repos.

hey, thanks for the input.  I remember the last time i got this working, when i typed make install, i had to specify a --prefix(new directory) but i don't remember the lodation... oh well.  thanks anyway!

---


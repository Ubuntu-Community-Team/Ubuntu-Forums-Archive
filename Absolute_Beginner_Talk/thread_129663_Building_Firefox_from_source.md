---
title: "Building Firefox from source"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by jofre on 2006-02-14
Hi lads, 

I am trying to build firefox from source:) . I downloaded the source and:
$ sudo tar -xjvf firefox-1.5-source.tar.bz2 -C /opt

I am following the step in:
[http://www.linux-sxs.org/internet_browsing/firefox_from_source.html](http://www.linux-sxs.org/internet_browsing/firefox_from_source.html)

The problem is that when i do:
 sudo make -f client.mk build

I get and error:
checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
*** Fix above errors and then restart with "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/opt/mozilla'
make: *** [/opt/mozilla/../firefox-build/Makefile] Error 2


I check in synaptic and it look to me that was already installed.:neutral:  

Any ideas?:-k 
Thanks, Jofre

---

### Post by heimo on 2006-02-14
One question... Why compiling and not using binary version? Not trying to argue, it's fine - you can do that, but maybe it's not neccessary (I don't know, but I guess this is appropriate question as you're posting in Absolute Beginner Talk forum).

---

### Post by jofre on 2006-02-14
I am just trying to learn. 

and also because for some strange reason, firefox is behaving very strange in my new computer.

Well, probably is not the correct thread to post this type of question....
I will try somewhere else.

---

### Post by heimo on 2006-02-14
I didn't have time to look through what could be wrong, but my guess is that running this command may help you:
```
sudo apt-get build-dep firefox
```

---

### Post by carlosqueso on 2006-02-14
Sorrry...myfirst post was stupid.....you probably need the gtk development files....I'm looking for them now.

---

### Post by jofre on 2006-02-14
I started a new thread in /Ubuntu 5.10 Support (GNOME). 

I think is a more adequated place.

Jofre

---


---
title: "problem compiling alsa-utils"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Geezle on 2008-02-13
Well I ran into the problem involving loss of sound on a new install like many others have.  i'm recompiling ALSA with the driver for my chipset (Intel HDA) but when I try to compile alsa-utils I run into problems.

./configure works fine, but when I try to make it, I get this:
```

jay@jay-desktop:/usr/src/alsa/alsa-utils-1.0.16$ sudo make
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.16/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.16/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.16/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1

```
I'm sure it's something simple, but what am I missing?

---

### Post by Blutack on 2008-02-13
You need to specify ./configure --prefix=/usr normally for ubuntu.
See if that helps.

---

### Post by Geezle on 2008-02-13
> **Blutack said:**
> You need to specify ./configure --prefix=/usr normally for ubuntu.
See if that helps.

I don't quite follow you.  I tried ./configure --prefix=/usr like you said and it compiled fine, but when I ran sudo make it gave me the same error.

I'm doing this following the instructions on the alsa project page here: [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

---

### Post by Geezle on 2008-02-13
Just to add something...right now when I go into my sound preferences, if I have everything set to autodetect or ESD Enlightened Sound Daemon the test sound will work, but I can't get my other sound programs working yet.  Hopefully I'll get this ALSA business configured soon and I'll be back in business :)

---

### Post by mab1376 on 2008-02-18
```
mark@mark-laptop:~/alsa/alsa-utils-1.0.16$ make
Making all in include
make[1]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/include'
make  all-am
make[2]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/include'
make[2]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1

```

i get this error...

---

### Post by seiffs on 2008-02-19
the solution is:

**aptitude install ja-trans gettext**

at least it worked for me

---


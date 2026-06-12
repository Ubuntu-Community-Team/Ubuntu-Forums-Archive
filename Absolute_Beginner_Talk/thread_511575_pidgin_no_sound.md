---
title: "pidgin no sound"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by tomcheng76 on 2007-07-28
i am using Pidgin 2.0.2 for Feisty 32bit
get it from [here]("http://www.getdeb.net/app.php?name=Pidgin")
i have no sound in Pidgin
already try aplay %s  and bplay %s
tested with aplay /media/drive/xxx.wav in terminal, and it works
any solution?

---

### Post by wolfen69 on 2007-07-28
you need a better computer.......just kidding.

---

### Post by tomcheng76 on 2007-07-28
i know it is not a gd computer , it always drive me nuts :(
btw,  anyone use pidgin complied from source?
could u post your ./configure parameter ?
i just want sound (i got gstreamer base and good, should be ok) and MSN protocol

---

### Post by tomcheng76 on 2007-07-28
pump
no one use complied pidgin ? :(

---

### Post by rendezvous123 on 2007-07-31
Interestingly enough, installing libgstreamer0.**08**-dev should fix the problem--it fixed mine.

This is my usual dep-installs: ```
sudo apt-get install libglib2.0-dev libgtk2.0-dev libxml2-dev libdbus-glib-1-dev libgstreamer0.10-dev libgnutls-dev tcl8.4-dev tk8.4-dev libgtkspell-dev libstartup-notification0-dev libxml-parser-perl gettext libsasl2-dev libgstreamer0.08-dev libxss-dev
```
Then, when you're **cd**'d in the pidgin source folder: ```
./configure --disable-doxygen --enable-cyrus-sasl && make && sudo make install
```
This covers everything i need, or should i say, want. :)

If you just want support for sound, MSN and GTalk, spelling-error and idle report, then: ```
sudo apt-get install libglib2.0-dev libgtk2.0-dev libxml2-dev libgstreamer0.10-dev libgnutls-dev libgtkspell-dev libxml-parser-perl gettext libgstreamer0.8-dev libxss-dev
```
Then: ```
./configure --disable-doxygen && make && sudo make install
```

P.S. If i made any spelling errors for the dependencies, please say so.

---


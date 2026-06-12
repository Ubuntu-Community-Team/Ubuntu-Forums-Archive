---
title: "Firefox wont update"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Gene07 on 2007-08-19
Hello, first time ubuntu user here, I recently installed 6.06 and have been trying to install the newest version of firefox. I went to the mozilla website and downloaded it and installed it, yet firefox is still on 1.5. I also used ubuntuzilla to update firefox, and yet it still says its on version 1.5 can someone help me?

---

### Post by aysiu on 2007-08-19
It sounds as if your symlinks are messed up somehow.

Let's start off by verifying that Ubuntuzilla installed Firefox 2.0 properly.

Can you paste these commands in the terminal and see if that launches Firefox? ```
cd /opt/firefox
ls
./firefox
```

---

### Post by AceofSpades19 on 2007-08-19
if you installed firefox from a tarball then you must run firefox 2 from the directory the tarball is in, by opening up a terminal and typing, 
cd (the folder the firefox 2 tarball is in)
./firefox

---

### Post by Gene07 on 2007-08-19
> **aysiu said:**
> It sounds as if your symlinks are messed up somehow.

Let's start off by verifying that Ubuntuzilla installed Firefox 2.0 properly.

Can you paste these commands in the terminal and see if that launches Firefox? ```
cd /opt/firefox
ls
./firefox
```

I pasted that and got this

gene@gene-desktop:/opt/firefox$ ls
browserconfig.properties               libsoftokn3.chk
chrome                                 libsoftokn3.so
components                             libssl3.so
defaults                               libxpcom_compat.so
dictionaries                           libxpcom_core.so
dictionaries_2007-08-19T22:05:58-0400  libxpcom.so
extensions                             libxpistub.so
firefox                                mozilla-xremote-client
firefox-bin                            old-homepage-default.properties
greprefs                               plugins
icons                                  plugins_2007-08-19T22:05:58-0400
libfreebl3.chk                         readme.txt
libfreebl3.so                          removed-files
libmozjs.so                            res
libnspr4.so                            run-mozilla.sh
libnss3.so                             searchplugins
libnssckbi.so                          updater
libplc4.so                             updater.ini
libplds4.so                            xpicleanup
libsmime3.so

---

### Post by aysiu on 2007-08-19
Okay. Now that you have that, type ```
./firefox
``` and see if it launches Firefox 2.0 or not.

---


---
title: "how to instaal wine after java runtime ????"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Aamir Aziz on 2007-07-13
i i've  installed the java runtime i.e. jre-6u1-linux-i586.deb  but it gives the errors: i.e.

(update-desktop-database:13294): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing j2re1.4 (--configure):
 subprocess post-installation script returned error exit status 139
Setting up wine (0.9.33-0ubuntu1) ...

Errors were encountered while processing:
 j2re1.4
E: Sub-process /usr/bin/dpkg returned an error code (1)


how can i install the wine ????

---

### Post by BobCFC on 2007-07-13
try opening the terminal in  Applications->Accessories->Terminal and typing

```
sudo apt-get remove --purge j2re1.4
```


then if that works install wine via
```

sudo apt-get install wine
```


Or just search for wine in add/remove programs.

---

### Post by Aamir Aziz on 2007-07-13
i've tried this:

sudo apt-get remove --purge j2re1.4

  but it doesn't work .. i've tried it from syneptic and add and remove also but this does not work ..

still wine is not installed ..

---

### Post by Aamir Aziz on 2007-07-13
still i have the same error i.e.


Errors were encountered while processing:
 j2re1.4

---


---
title: "Help me install YAHOO Messenger plz"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by namith on 2006-02-12
[FONT="Arial"]i tried installing the yahoo messenger package.
but i got some errors. this is wat came in the terminal wen i tried installing the package[/FONT]

root@euclid:/home/namith/Desktop# dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 75967 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

---

### Post by vialick on 2006-02-12
I'm not totally sure, but it looks to me like you also need to install the following packages or YIM won't work

libgdk-pixbuf2
libglib1.2
libgtk1.2
libssl0.9.6

if you get those packages (should be easy via apt-get) YIM should install properly

unless I'm horribly mistaken

---

### Post by sabitha on 2006-02-12
try with simple code:
$ sudo apt-get -f install
\\:D/

---

### Post by sailor2001 on 2006-02-12
or click 'gaim'

---

### Post by HiSpeed15 on 2006-02-12
GAIM worked  for me,just click  it enter your yahoo id and there ya go. 
Same with ICQ just add your ICQ # and password ..and "poof" done! Havent used that MSN Messenger junk for years so i'm not even sure if it works or why anyone would bother LOL
 Gaim may not be as "pretty" as YM but seems as functional.

---

### Post by byen on 2006-02-12
namith. As you can see with the common opinion... gaim is a better option here. But to answer your question.. do what sabitha has suggested. Not just for this program but while installing any debs from terminal... you usually do

sudo dpkg -i packagename.deb
sudo apt-get -f install

The first installs the programs and informs abt missing packages
The second command installs the missing packages and completes the installation.
Hope that helps. Goodluck!

---


---
title: "Upgrading ubuntu problem"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2005-10-22
When updating my ubuntu from horay to breezy I got this as an error.  

Errors were encountered while processing:
 /var/cache/apt/archives/kdevelop3-data_4%3a3.2.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

then it stopped.  I am going to try to run 
sudo apt-get dist-upgrade 
again.  If anyone knows what that means please help me.

EDIT

I ran it again and now i got htis error
Unpacking replacement lsof ...
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ran it agian and now i got this.

Unpacking replacement kbruch ...
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now i got the same thing except with arts.  But slowly im getting through everything... its wierd ... i may just do  fresh install

I kept on trying to do it and it was working and it was getting further and further. but now it doesn't go any further.  It keeps getting stuck here.

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 116748 files and directories currently installed.)
Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Thanks again,
Hans

---

### Post by hansoffate on 2005-10-22
bump

---

### Post by Kapre on 2005-10-23
[QUOTE=hansoffate]bump[/QUOTE]

hansoffate - just wondering if you changed all the repos in your sources.list from Hoary to Breezy? Maybe it's the one that is causing the problem.

K

---


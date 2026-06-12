---
title: "Please Insert the Disc Labelled 'Ubuntu-Server 7.04 ..."
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by dc.manage.service on 2007-09-09
Hi there

I'm trying to install SSH server into Ubuntu Server and I got the message saying "Please Insert the Disc Labelled 'Ubuntu-Server 7.04 ..."

I went to forum and I saw that I need to check out /ect/apt/sources.list and get rid off the comment out for cd-rom:

I saw that first line like this:
#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

They aren't comment out ... are they? 

Thanks

---

### Post by aysiu on 2007-09-09
The first one is commented out. The second one isn't.

Commented out: ```
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
``` Not commented out: ```
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
``` Just put a # sign at the beginning of the line.

---

### Post by dc.manage.service on 2007-09-09
Ah ... it suppose to be comment out. I thought the other a way around.

Thanks

---


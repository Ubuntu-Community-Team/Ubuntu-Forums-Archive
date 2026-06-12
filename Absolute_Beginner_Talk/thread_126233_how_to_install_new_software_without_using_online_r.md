---
title: "how to install new software without using online repository"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by ramaadhitia on 2006-02-06
i want  to install zinf a mp3 player for linux.so i use the "make -install" command but i was very surprised that the "make "command doesn't exist in ubuntu.Any idea to solve this problem?

---

### Post by myha on 2006-02-06
Well, if you want to compile it manually you usually have to do
./configure
make
make install

But you have the program in the repository so I don't see any need for compiling it manually...
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zinf&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zinf&searchon=names&subword=1&version=breezy&release=all)

br

edit:When you extract files you usually have INSTALL file in it which gives you all the information you need....

---

### Post by Klaidas on 2006-02-06
When compiling, you must have a "build-essential" package :)

---


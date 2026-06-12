---
title: "absolute newbie: how to install programs like cvs, gcc, make"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by laptin on 2006-02-04
I installed linux to do some programming
but i am very new to linux.

i just want to get the gcc, cvs, make working.
i downloaded the files(i think is the right one), how can i install them?
please teach me step by step. like..how to install "make"

---

### Post by laptin on 2006-02-04
the make file i download is called: make_3.80-8_i386.deb
and when i try to open it, it says .deb is not supported..

---

### Post by Qrk on 2006-02-04
```
sudo apt-get build-essential
```

this will download all or most of the tools you need.

---

### Post by Madpilot on 2006-02-04
Open Synaptic (**System menu --> Administration --> Synaptic Package Manager**) and search for "build-essential" - that should install all the compilers you need.

(When Synaptic asks for a password, use your own user password)

---

### Post by Adrian on 2006-02-04
[QUOTE=laptin] like..how to install "make"[/QUOTE]

First of all, read this document about how to install software in Ubuntu:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

You usually don't have to download .debs and install manually. For instance, to install **make** run Synaptic (explained in the document I linked to) and install the **build-essential** package. This package includes make, gcc and g++ amongst others.

It's 5 AM here in Sweden now, so I really have to go to bed. If you have more questions, and noone else answers until then, I'll try to reply when I wake up tomorrow.

*Edit: I guess I am not typing fast enough tonight :)*

---

### Post by laptin on 2006-02-05
thank you all of you... all of those are very HELPFUL.  and they worked!!

:)

---


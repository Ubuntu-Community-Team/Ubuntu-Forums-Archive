---
title: "modemless"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by magicbastard on 2005-12-02
my computer doesnt have a modem but I want to install some games and updates.  Can I download them onto a cd and run them on ubuntu or am I screwed?  Thanks

---

### Post by dalee on 2005-12-02
Hi,

No, not necessarily. If you can download and burn or copy to some storage media that works on both systems, you can open a term and type "cd /directorywhereprogramis/", then type "sudo dpkg -i packagename.deb" It should install IF no dependencies need to be filled in. If that happens, then you will need to go back and get all the deps and install them too.

It can be done, but it can be quite a chore to do it if any dependencies are needed. It really is best to have an interent connection setup and working.

dalee1002000

---


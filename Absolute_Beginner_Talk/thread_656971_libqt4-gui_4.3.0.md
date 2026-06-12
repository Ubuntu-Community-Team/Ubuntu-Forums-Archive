---
title: "libqt4-gui 4.3.0"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mongoose_za on 2008-01-03
hi

i want to upgrade my libqt4-gui 4.2.3 to libqt4-gui 4.3.0
but in synaptic it says i've got the latest version? what's going on?
i guess i have to update the source list but not quite sure what to type there?

---

### Post by n8bounds on 2008-01-03
Why exactly, if I may ask?

---

### Post by mongoose_za on 2008-01-03
course you may.. if you can help ;)
i want to use acetoneISO2 but for some reason it doesn't start up. I emailed the guy and he told me i need libqt4 4.3.. the one that comes with ubuntu is not 4.3. there is an option to install the KDE copt of libqt4 4.3.. but then it says it wants to delete a lot of stuff off my machine... i'm not comfortable with that so i wanna know if perhaps it's the original ubuntu file i need to update or whether i must just click libqt4 4.3.0 KDEcopy and delete the other stuff.

---

### Post by ~LoKe on 2008-01-03
That version is simply not in the repositories.  Perhaps you could download the source for it and compile it yourself.

**EDIT**: You could always update to Gutsy Gibbon (7.1), it has libqt-gui 4.3.2.

```
[14:06:02 loke]$ sudo dpkg -l libqt4-gui
||/ Name                       Version                
===============================================
ii  libqt4-gui                 4.3.2-0ubuntu3.1       
```

---

### Post by bulletxt on 2008-01-04
completely wrong. ubuntu feisty has libqt4 4.3. just enable feisty-backports repository.

or go here and download it...very simply:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libqt4&searchon=names&subword=1&version=feisty-backports&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libqt4&searchon=names&subword=1&version=feisty-backports&release=all)

---

### Post by mongoose_za on 2008-01-07
bulletxt
how do i enable fiesty backports repositries. sorry for being noob :/

---

### Post by prophetkinggov on 2008-01-16
In Synaptic:

Go to the **Settings Menu** and click on **Repositories** . Hit the **Updates** tab and look through the options. You'll find the box you need to check there.

*Edit: Oh, and **Reload** your Synaptic when done.*

---


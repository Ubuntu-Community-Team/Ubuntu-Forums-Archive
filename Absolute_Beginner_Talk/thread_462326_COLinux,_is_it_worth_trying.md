---
title: "COLinux, is it worth trying?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-06-02
[Colinux]("http://www.colinux.org/") is a program intended to run a Linux distro and MS Windows at the same time on the same desktop. I'm interested to try it and see if I can get the games to run with directX and Office 2007 too.

Has anyone in this forum ever tried it? What is your impression?

---

### Post by H.E. Pennypacker on 2007-06-02
I would advice you use VirtualBox to run Windows on Ubuntu.  I don't know anything about Cooperative Linux to say anything about it, but you can at least be sure that you'll get some help if you use VirtualBox, because there are other VB users on this message board.

---

### Post by kevinlyfellow on 2007-06-02
Give it a shot!

---

### Post by the8thstar on 2007-06-02
Is directX active with COLinux? Can Office 2007 run with COLinux?

---

### Post by bodhi.zazen on 2007-06-02
> **the8thstar said:**
> [Colinux]("http://www.colinux.org/") is a program intended to run a Linux distro and MS Windows at the same time on the same desktop. I'm interested to try it and see if I can get the games to run with directX and Office 2007 too.

Has anyone in this forum ever tried it? What is your impression?

Yes ....

Colinux allows you to run Linux on Windows as a guest.

You will need to install cygwin on windows if you want X applications :

Cygwin : [http://www.cygwin.com/](http://www.cygwin.com/)

Then you ssh into your Linux guest and forward X to windows.

If you want to go fast and easy go with VMWare server or VirtualBox.

You can also go qemu if you want an intermediate approach.

If you go colinux you will learn a lot very fast :)

BUT colinux will not allow you to run windows in Ubuntu (other way around).

---

### Post by bodhi.zazen on 2007-06-02
> **the8thstar said:**
> Is directX active with COLinux? Can Office 2007 run with COLinux?

Yes because you run those programs on your windows host :)

---

### Post by the8thstar on 2007-06-02
Hmm... I would rather have windows as the guest

---

### Post by bodhi.zazen on 2007-06-02
> **the8thstar said:**
> Hmm... I would rather have windows as the guest

Bodhi hands the8thstar VirtualBox : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by apoth on 2007-06-03
It was a mess when I last tried it. You're better off with something like VMWare.

---


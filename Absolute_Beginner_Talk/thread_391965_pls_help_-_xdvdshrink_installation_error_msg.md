---
title: "pls help - xdvdshrink installation error msg"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by johnlh on 2007-03-23
I received the following error msg during xdvdshrink installation.  I've been digging around, but still not sure what it means and how to fix it.  Thanx in advance. :)

sudo alien dvdshrink-2.6.1-8mdk.noarch.rpm
Warning: Skipping conversion of scripts in package dvdshrink: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
dvdshrink_2.6.1-9_all.deb generated

---

### Post by johnlh on 2007-03-23
never mind... found the answer.

---

### Post by stchman on 2007-04-02
> **johnlh said:**
> I received the following error msg during xdvdshrink installation.  I've been digging around, but still not sure what it means and how to fix it.  Thanx in advance. :)

sudo alien dvdshrink-2.6.1-8mdk.noarch.rpm
Warning: Skipping conversion of scripts in package dvdshrink: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
dvdshrink_2.6.1-9_all.deb generated

Install k9copy.  I gather you want to backup encrypted DVDs.

sudo apt-get install k9copy

It does the exact same thing as DVDShrink.  Follow the steps on my webpage:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This will get CSS decryption up and going on Ubuntu.  After k9copy is done decrypting and compressing it will burn it to a DVD using k3b or just create a .iso.

---


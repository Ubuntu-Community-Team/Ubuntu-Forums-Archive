---
title: "memory stick security protection"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by nicdal on 2007-07-11
How can I password protect [or make secure somehow, if used by others] a memory stick - USB storage device, call it what you want - which is used to carry stuff from my smashing Ubuntu laptop to my creaky Windows '98 desktop and vice-versa ?

---

### Post by Vajra Vrtti on 2007-07-11
Short answer: [TrueCrypt]("http://www.truecrypt.org/").
I do that. Please post, if you need more help in this matter.

---

### Post by Vajra Vrtti on 2007-07-11
I'm sorry! TrueCrypt does not support Windows 98.

---

### Post by nicdal on 2007-07-15
> **nicdal said:**
> How can I password protect [or make secure somehow, if used by others] a memory stick - USB storage device, call it what you want - which is used to carry stuff from my smashing Ubuntu laptop to my creaky Windows '98 desktop and vice-versa ?

In answer to my own question: the best thing I've come up with is to create a password protected *.zip file in Archive Manager in which to transport stuff. WinZip in windows handles things properly, requiring password for extraction of files.

---

### Post by Vajra Vrtti on 2007-07-15
> **nicdal said:**
> In answer to my own question: the best thing I've come up with is to create a password protected *.zip file in Archive Manager in which to transport stuff. WinZip in windows handles things properly, requiring password for extraction of files.
In security related issues you have always to consider from whom you want protection. Zip passwords are a protection against a casual sniffer, but a weak one. It's easy to brake ([first answer]("http://www.lostpassword.com/zip.htm") in Google for "zip password crack"). If file encryption is adequate for you, then [GnuPG]("http://www.gnupg.org/") is probably the most robust solution you can have. Although it has a command line interface, there are [GUI]("http://www.gnupg.org/(en)/related_software/frontends.html#gui")s for it.

---


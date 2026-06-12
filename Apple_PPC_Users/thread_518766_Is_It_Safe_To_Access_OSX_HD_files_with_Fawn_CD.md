---
title: "Is It Safe To Access OSX HD files with Fawn CD?"
date: 2007-08-06
forum: Apple PPC Users
---

### Post by jimwg on 2007-08-06
Greetings:

I have Mac OpenOffice files on my 10.4.10 formatted HD that I'd like to use my Live-CD Fawn's OpenOffice on, but I just want to be sure that it's safe for Fawn/Linux to access read/write docs on a OS-X formatted HD.

Thanks.

JimWG

---

### Post by BoneKracker on 2007-08-06
Yes.  Be careful not to change file ownership.

---

### Post by jimwg on 2007-08-06
> **BoneKracker said:**
> Yes.  Be careful not to change file ownership.

Okay, I'm not a techie. If I save a Linux/Fawn OpenOffice document on my HD, will its "ownership" be Linux OpenOffice?

Thanks,

JimWG

---

### Post by stmiller on 2007-08-06
Access to an OS X partition will be read only by default. So it's fine and safe to access data on that drive, but you have to turn off journaling (in OS X), and install some hfs tools to be able to write.

---

### Post by jimwg on 2007-08-07
Thanks for that info!

JimWG

---


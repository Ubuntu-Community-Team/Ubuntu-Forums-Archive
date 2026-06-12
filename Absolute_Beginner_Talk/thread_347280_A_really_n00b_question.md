---
title: "A really n00b question"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tbasherizer on 2007-01-27
I've been using Ubuntu for a while now, and I still haven't figured something out. How do I tell the difference between my local hard drives? In the filesystem, there is no distinguishing factor between my D and C drives (in WinDoze)

---

### Post by oldmanstan on 2007-01-27
the filesystem icon is the harddrive that you installed ubuntu on.  "filesystem" IS your harddrive, only one of them.  unless of course you have your /home set up on a separate partition/drive, but you probably don't

your other drive(s) should show up under the "places" menu

the reason you can access other drives from "filesystem" (which is just your root, / in the command line) is that the contents of your other drives are linked to directories in your root filesystem, you access other drives through your root filesystem rather than accessing the device directly.

your other drives should show up under /media

look for hdxx where xx are a letter and a number

---

### Post by randomnumber on 2007-01-27
This thing about not knowing local drive or not is a good thing. Say you are a student at a school that has central storage for your files. The storage gets mounted at login. You do NOT care where the data is. That is not something you should know or care about, you just know that when you sit at any computer at the school and login you and you alone have access to your data.

Knowing where the data is fiscally located is an administrative need to no info, not user need to know.

Just thought you would like to know that.

---


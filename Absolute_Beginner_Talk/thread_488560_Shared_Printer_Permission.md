---
title: "Shared Printer Permission"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Tommy James on 2007-06-30
I have to put this one out to the team here.

Can you guys help me get my XP box to print on my xubuntu connected printer? I believe I have a permission issue.

I've searched, googled, and read for 2 days looking for the answer and can't find it. Tried a ton of how to's, tips, you name it.

There are 3 systems in my network all on the same router. 1) Ubuntu 7.04, 2) xubuntu 6.06 - Lexmark printer USB attached, 3) Windows XP (work laptop). Set up Samba and CUPS per some great how to's on this forum.

Filing sharing is completed. All boxes can read, write, create, delete files and folders going every way you can name.

Ubuntu box printers to the xubuntu attached printer no problems.

On the Windows XP box, I can see, install, config, everything on printer; but I can't print - test pages, or anything. When I print from Notepad I get an error - "A StartDocPrinter call was not issued." I installed it by clicking on the share. Setting up the URL "http://xxxxx:631/xxxxx stated I cannot access the printer.

One how to recommended doing Start->Run:\\myserver\print$ Once there try to create a folder. Access was denied so I must have a permission issue, right?

Looking for some help.

Thanks everyone!!!

---

### Post by Tommy James on 2007-07-01
Any thoughts?

---

### Post by Tommy James on 2007-07-02
Really, no one has any ideas on how to fix this?

---

### Post by tarek on 2007-07-02
You said that you installed samba, so open /etc/samba/smb.conf and look for "cups" and remove the # from the beginning of these lines like this:

```

......
# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
    printing = cups
    printcap name = cups
......

```

then restart samba:
```
sudo /etc/init.d/samba restart
```

tk

---


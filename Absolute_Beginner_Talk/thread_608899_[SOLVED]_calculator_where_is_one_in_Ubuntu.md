---
title: "[SOLVED] calculator where is one in Ubuntu?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-11-10
Where is the calulator in Feisty?

I thought it was in applications/accessories

but it is not there, so where is it?

robi

---

### Post by trak87 on 2007-11-10
applications/accessories

That's where it is in my Feisty menu.

Or, type Alt-F2, gcalctool

You can also do something like this:

```
$ slocate -ir bin.*calc
```

and it gives four results:

```
/usr/bin/xcalc
/usr/bin/gcalctool
/usr/bin/gnome-calculator
/usr/bin/oocalc

```

gcalctool is the same as gnome-calculator and the last one, oocalc, is the OpenOffice Spreadsheet application.

---

### Post by Pumalite on 2007-11-10
If it's not there, you might have a defective installation. Anything else doesn't work?

---

### Post by beanco on 2007-11-10
i must be blind, i went back and checked and it wqas there... 

but what is weird is I had checked twice before!!!

I ned some sleep.

---


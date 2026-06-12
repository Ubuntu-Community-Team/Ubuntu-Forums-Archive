---
title: "Ubuntu Fiesty User settings not available"
date: 2007-05-06
forum: Apple PPC Users
---

### Post by grammataki on 2007-05-06
Ive recently installed Fiesty Ubuntu and after updating the software, have found I cannot acces the user settings control panel and time through administration.  Have searched 6this forum and the web for potential answers but to no avail.  Have tried many solutions but to no avail.  Can anybody direct me to a solution.  Thank you.

Grammatis

---

### Post by NilsE on 2007-05-06
Go to System/Preferences/Main Menu then under Preferences select Control Center to add it to the System Tools  menu

However, the reason it is not selected by default is that all the entries in it are already on the System menu so it is redundant.

If you are talking about the Configuration Editor (gconf-editor) you need to make that available on the Systems menu under System tools

---

### Post by ssam on 2007-05-06
is the user you are logged in as in the admin group?

some control panels are hidden from non admin users.

open a terminal and type
```
id
```
to see which groups you are in.

---


---
title: "[SOLVED] Printing Spreadsheet issue - Open Office Calc"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by tdmoore on 2008-01-15
Looking for some help with a printing issue.

Running Gutsy 7.10, have an HP 1000 running fine for all print jobs however tonight with a particular spreadsheet it would not print.  Converted to PDF however it printed fine in Evince.

No security issues with the file and it printed fine in Windows.  Please note that I use Open Office both at home and in our work environment (for several years now) and have never seen this before.  Version of OOo is 2.3.0.

Page was legal, print ranges defined and page preview showed both the main page as well as the notes that were going to be printed on page 2.

Although it printed correctly via Evince, any suggestions as to why this happened?  Concerned there is an issue with how it is set up.

Please note that I am not good at all with command lines...do know it printed through CUPS.

Thanks in advance!

---

### Post by polmir on 2008-01-15
Install this package *(terminal)*
```
sudo apt-get install foo2zjs
sudo apt-get install foomatic-db
sudo apt-get install foomatic-db-engine
sudo apt-get install foomatic-db-hpijs
```

After this operation reinstall driver of printer

---


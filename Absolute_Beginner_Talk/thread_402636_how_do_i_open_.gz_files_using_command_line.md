---
title: "how do i open .gz files using command line?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by richieboy on 2007-04-06
i want to read the manual for gnuchess.  it is a .gz file.  the gui tells me i don't have permission to extract so i need to sudo on the command line.  but i don't know the command!  dang1  can someone help please?

thanks,
rich

---

### Post by gilforsyth on 2007-04-06
```
sudo gunzip filename.gz
```

if you don't have gzip, then
```
sudo apt-get install gzip
```

---

### Post by richieboy on 2007-04-06
THX!  that worked.

---

### Post by gilforsyth on 2007-04-06
glad to help

---

### Post by aysiu on 2007-04-06
If you want to extract something to a system folder, you can extract it to your home folder and then move it over to the system folder using [this tutorial](http://www.psychocats.net/ubuntu/permissions).

You can also install GnuChess by [enabling extra repositories](http://www.psychocats.net/ubuntu/sources) and then pasting this command into the terminal: ```
sudo apt-get update && sudo apt-get install gnuchess gnuchess-book
```

---


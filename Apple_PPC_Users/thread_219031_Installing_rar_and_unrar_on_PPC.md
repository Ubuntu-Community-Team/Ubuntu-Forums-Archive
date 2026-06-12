---
title: "Installing rar and unrar on PPC??"
date: 2006-07-19
forum: Apple PPC Users
---

### Post by tdos20 on 2006-07-19
I have been trying to uncompress a .rar archive, I've tried the rar support from winrar but there is no PPC architecture build, is ther e a program which can do the same using Java or some other program which works on PPC? :confused: 
I'm only interested in unrar-ing files, I'll use a more standard format.
I'm running Dapper on a G3 Blueberry :rolleyes:

---

### Post by mogelhead on 2006-07-19
To extract rar files you first need to enable the multiverse repository: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu). There you also can read about what a repository is and what the differences are between main, universe and multiverse.

Then you need to install unrar by pasting this into a terminal window (and hit enter):
```
sudo apt-get install unrar
```

Bonus information, feel free to ignore this part:
There is a unrar-free package in the universe repository, but it `Can't handle archives in the RAR 3.0 format, only the non-free "unrar" package [in the multiverse repository] can do that`

---


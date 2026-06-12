---
title: "Part. Size And Wireless"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by evolving on 2007-01-20
I am installing Dapper Drake (hope that is the right name) for my first Linux experience and have already received a great deal of help from this community.  I have been reading, reading, reading.  More I read, the more I don't know.  

Anyway, I am about to actually move from Live to Installed Ubuntu on my laptop.  I have a Dell Latitude D610 computer with a 30 GB hard drive of which 20 GB is free space.  I am planning to continue using Windows for my work stuff until I can competently switch over to Linux.  So, I am wondering what a recommended partition would be for Ubuntu.  Any suggestions would help.

Also, in using the Live CD, I have not been able to use my wireless internet connection.  Instead, I have needed to plug in the ethernet cord.  I have a dell wireless card and I presume I need the equivalent of a driver.  Any suggestions would be useful.

Thanks again.

---

### Post by moshuptrail on 2007-01-20
For starters, on the partition size, I'll just hazard a guess:
Windows 18G (leaves plenty of room to work)
Linux Swap .5G (needs to be 2x memory)
Linux main (/)  5G ext3
Linux user (/home) 5G ext3

do some rounding depending on your needs.

As to the wireless - that's going to take some work, and studying, if it didn't auto-configure in the Live CD.
Start a new post on that when you're ready.

---

### Post by mikewhatever on 2007-01-20
5 GB for the swap :biggrin: I'd say that's an awful waste of space.

---


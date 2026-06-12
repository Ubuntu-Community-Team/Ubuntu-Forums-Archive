---
title: "Another AirPort Wireless Thread - Trouble with ndiswrapper"
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by SteveRonan118 on 2008-05-02
I have tried getting the proper drivers and installing them with ndiswrapper.  Unfortunately, I can't seem to get it to work.  The chip is the Atheros 5418, which according to what I've found, should require the ar5416.sys driver, with the net5416.inf and net5416.cab files.  I have all these, but I cannot seem to get my drivers properly installed.

I try: *sudo ndiswrapper -i net5416.inf*   
and get:
*couldn't open NET5416.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.*

Then if I type *ndiswrapper -l*     I get:
*net5416 : invalid driver!*

Thank you very much in advance for your help.

Steve

---

### Post by antono on 2008-05-02
> **SteveRonan118 said:**
> 
I try: *sudo ndiswrapper -i net5416.inf*   
and get:
*couldn't open NET5416.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.*

I have following files in my /etc/ndiswrapper:

-rw-r--r-- 1 root root 1.3M 2008-04-26 15:22 ar5416.sys
-rw-r--r-- 1 root root  24K 2008-04-26 15:22 net5416.inf

Both have lowercase extensions.

I suppose ndiswrapper doesn't understand uppercase .inf extension. I'am not perl programmer but regular expression at line 181 (s/\.inf//) doesn't expect uppercase.

Try to rename this binary crap to lowercase and import them once more. 

PS: Have you ever heared about ndisgtk?

---

### Post by cyberdork33 on 2008-05-02
remove the non-working driver first with ndiswrapper -r

---


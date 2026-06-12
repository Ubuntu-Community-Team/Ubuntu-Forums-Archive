---
title: "Blacklisting?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-20
**For what im trying to do i was told to do this:**
So you need to blacklist it first in a file situated in etc/modprobe.d/


Code:
$sudo gedit /etc/modprobe.d/blacklistadd the following line in the blacklist file 





**I have no idea this means.  Can someone help me in telling me how to blacklist a file?**

---

### Post by skot on 2007-03-20
try this....
```

sudo gedit /etc/modprobe.d/blacklist

```

the type what he says to add. example "blacklist asdfghjk" minus quotes.  save the file then reboot.

im having the same issue.  but when i goto save it wont let me.
try it and write back if you can save it.

---

### Post by scxtt on 2007-03-20
try:

gksu gedit /etc/modprobe.d/blacklist

---

### Post by skot on 2007-03-20
> **scxtt said:**
> try:

gksu gedit /etc/modprobe.d/blacklist

oops i forgot to tell him the gksudo part.

---

### Post by zeroo on 2007-03-20
No I mean I have absolutly no idea how to do it. It said the file is situated in  in etc/modprobe
how do i find this? I've never used linux before please help.

---

### Post by skot on 2007-03-20
applications>terminal.
then type into that.

---

### Post by scxtt on 2007-03-20
**So you need to blacklist it first in a file situated in etc/modprobe.d/**
/etc/modprobe.d/ is a directory where a file called "blacklist" is located - this is the file the command below will allow you to edit ...

***gksu* gedit /etc/modprobe.d/blacklist # add the following line in the blacklist file **
that command will allow you to add the name of the module you want to blacklist, so when gedit pops up - type in the name of the module and hit SAVE

---

### Post by zeroo on 2007-03-20
Okay Im in the terminal.  When i attempt to search for the file it says no such file or directory.  The line before I type says desktop.  I believe this means that it is searching the desktop.  If this is indeed the problem then how do I change this so it searched every where on my computer?

---

### Post by scxtt on 2007-03-20
in a terminal:

**sudo nano /etc/modprobe.d/blacklist**
(enter your password, and no - it doesn't echo back what you type or give your ***s)

enter the name of the module @ the bottom of the file

**ctrl+o**: to save the file
**ctrl+x**: to exit from nano

---

### Post by zeroo on 2007-03-20
Oh, okay thankyou.  This is exactly what I needed.


Thanks.

---


---
title: "burning and blanking in xfburn is this a cure for you?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2007-05-19
Hi all,
     I've read in the forums of people having problems with xfburn and wodim ,this may be a cure it seems to be working for me.

sudo chmod 4755  /usr/bin/wodim
sudo chmod 4755  /usr/bin/X11/wodim
sudo chmod 4755  /usr/bin/cdrdao
sudo chmod 4755  /usr/bin/X11/cdrdao

sudo adduser  USERNAME  cdrom

I can write and blank cdrw with this hope it helps

Philj
Xubuntu 7.04

EDIT
also added the following line to  /etc/wodim.conf it may or may not make a difference to you

default=    ATAPI:0,0,0        -1      -1   burnfree

got the information from scanbus using cdrdao as it read the info better than  cdrecord scanbus 

cdrdao scanbus 

End of edit

---

### Post by PhilJ on 2007-05-19
bump for an edit

---


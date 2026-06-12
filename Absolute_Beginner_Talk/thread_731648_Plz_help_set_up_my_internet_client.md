---
title: "Plz help set up my internet client"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by ksr4a0 on 2008-03-22
i'm an absolute newbie...I installed Ubuntu 7.04 one day back(dual boot-windows xp sp2)....
My internet is a cable connection for which i have to first login thru a client software....i downloaded the linux version of it thru windows xp.....it is of format tar.gz....it has  2 files---one is a readme and the other is a .exe file....plz tell me how to install this....i hav placed it on my desktop in ubuntu....i am unable to install it thru synaptic or wine....i need to install it & log in thru it to connect to the web 

....i am attaching the tar.gz file that i need to install

---

### Post by SomethingCronic on 2008-03-22
```
sudo ./crclient
```

(at a guess, not in Linux at the moment)

If it has been activated via Windows I wouldn't have thought you need to do it again in Linux.

---

### Post by ugm6hr on 2008-03-22
Does this help?

[http://kb.cyberoam.com/print.asp?id=389&Lang=1&SID=](http://kb.cyberoam.com/print.asp?id=389&Lang=1&SID=)

---

### Post by ksr4a0 on 2008-03-22
i saw the link given by you ([http://kb.cyberoam.com/print.asp?id=389&Lang=1&SID=](http://kb.cyberoam.com/print.asp?id=389&Lang=1&SID=) )....when i entered the command "tar xvfz CyberoamLinuxClient.tar.gz"  two files got extracted.....but then when i enter the next command "./crclient -u username"  i am getting a message as "bash: ./crclient: is a directory"....plz help me out

---

### Post by SomethingCronic on 2008-03-22
```
cd crclient
```

then run the command above. You've untar'd the file but you've not accessed the directory that it creates.

---


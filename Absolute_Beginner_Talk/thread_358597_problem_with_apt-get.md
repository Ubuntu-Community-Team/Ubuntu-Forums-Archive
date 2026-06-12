---
title: "problem with apt-get"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kadhol on 2007-02-11
Hi, i'm beginner in linux, i run command apt-get update and i update libdns21, after that when i run again command **apt-get update**  show error : 

Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing libdns21 (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


how to fix this problem, plz guild me :)

---

### Post by brucehohl on 2007-02-11
I had a similar problem once that I caused by installing a bad package using dpkg tool.  The problem went away after I removed the package so:

You could try to remove libdns21:
# apt-get remove libdns21

Then check if "apt-get update" will work.
Now try to install libdns21
# apt-get install libdns21

---

### Post by kadhol on 2007-02-11
ok.. i run command ... 

root@server:~# apt-get remove libdns21
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing libdns21 (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
root@server:~#


it wont work :(

---

### Post by moore.bryan on 2007-02-11
[I]what about trying it with aptitude... it's just another front for apt, but it's resolved a lot more problems on my machine than apt-get in the past...
```
sudo aptituude update && sudo aptitude remove libdns21
```
if it works, try reinstall with aptitude:
```
sudo aptitude install --with-recommends libdns21
```
[/I]

---


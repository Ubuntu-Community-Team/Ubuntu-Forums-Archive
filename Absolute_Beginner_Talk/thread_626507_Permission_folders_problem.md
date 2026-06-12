---
title: "Permission folders problem"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by spyblue on 2007-11-29
Hello people.

I tryed this command: sudo mkdir -p /usr/run/firebird and it´s ok but when i restart my system this folder are not there. Why it happen ?

It´s one of my problems to start my firebird server. I get start type commands but not on boot. :(

My system are Ubuntu 7.10 and firebird 2.0 super server

Thank´s
From Brasil

---

### Post by vanadium on 2007-11-29
Check whether the directory was properly created: 1) you should have no error message 2) "ls -l /usr/run | grep firebird" should show the name and details of the created directory.

If it is gone again upon restart, then something is deleting the directory. Check by starting up without starting firebird server, see if the directory is there, start firebird manually, note error messages and check whether directory is still there after starting firebird. This will allow to narrow down where the problem is.

---

### Post by spyblue on 2007-11-29
Hello people !! Something are deleting the directory.. now i don´t know what are deleting. It´s really broking my head.. it´s so strange behavior. :confused:

Directory are created and after restart it are not there.. disappear

I will try again starting of 0 to install firebird but i think it´s one Ubuntu problem.. anyway strange problem. :(

Thank you

---


---
title: "Help with Zinc"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by whitehawk on 2006-02-11
I just got Ubuntu 5.10 up and running and I am new to linux . I have just installed Zinc and the java aplet that was need  when I  start zinc I did this at the command prompt  I get this error 

username@ubuntu:~$ zinc
Traceback (most recent call last):
  File "/usr/bin/zinc", line 42, in ?
    zinc.start()
  File "/usr/lib/zinc/Zinc.py", line 137, in start
    self.sess.load()
  File "/usr/lib/zinc/Session.py", line 313, in load
    self.login.load()           # load login
  File "/usr/lib/zinc/Login.py", line 307, in load
    roomnum = proflist[7].strip()
IndexError: list index out of range
 can someone tell me how to fix 
Thanks

---


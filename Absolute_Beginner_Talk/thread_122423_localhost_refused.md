---
title: "localhost refused"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2006-01-27
What could the reason?

andy@localhost:~$ sudo telnet localhost 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
andy@localhost:~$

hc:) :)

---

### Post by bscbrit on 2006-01-27
Is telnetd installed?

---

### Post by Hotchilli on 2006-01-27
thanks for your post

i tried apt-get install telnetd did not work,
but cannot think what the password might be as the only one I 
have is what I log on with. that did not work

So I tried 

 * Restarting OpenBSD Secure Shell server...                             [ ok ]

andy@localhost:~$ sudo ifconf
sudo: ifconf: command not found
andy@localhost:~$ sudo telnet localhost 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
andy@localhost:~$ sudo ssh localhost 25
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 60:e1:00:3d:ed:f6:ee:87:2a:47:1a:87:82:5a:38:72.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
root@localhost's password:
Permission denied, please try again.
root@localhost's password:
Permission denied, please try again.
root@localhost's password:

---

### Post by bscbrit on 2006-01-27
I found it under synaptic so I suppose I could have different repos to you.

---

### Post by bscbrit on 2006-01-27
Got it - you are trying to telnet using sudo?  In which case it will keep asking you for your root password which doesn't exist, therefore you cannot log on.  Try telnet'ing as yourself (normal user) and see what happens.  You will find that there is a setting (I forget where!) which forbids connections as root.

---


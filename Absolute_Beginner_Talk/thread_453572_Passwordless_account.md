---
title: "Passwordless account?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-24
Is there any way to create a user account without a password?
I want to use this for my sshd, so the guest account has no password.

Thanks!

Dr Small

---

### Post by Darryl Ring on 2007-05-24
```
$ sudo passwd -d USERNAME
```

According to the man page the -d option deletes the password. I don't know if this also locks the account so be careful.

Passwordless accounts are just bad news.

---

### Post by Cypher on 2007-05-24
Rather than create an account with any password for SSH purposes, you should go about it the right way and use authenticating DSA/RSA keys on the client and server which will allow you to securely login, but not require a password.

Follow the instructions on any of these websites:
[http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html](http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html)
[http://www.cs.umd.edu/~arun/misc/ssh.html](http://www.cs.umd.edu/~arun/misc/ssh.html)
[http://www.linuxproblem.org/art_9.html](http://www.linuxproblem.org/art_9.html)

---


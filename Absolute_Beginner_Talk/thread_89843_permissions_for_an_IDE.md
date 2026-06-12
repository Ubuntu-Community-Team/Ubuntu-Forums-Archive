---
title: "permissions for an IDE"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2005-11-13
I want to edit the files for my web user - but im running the program from my username - is there some way to sudo the program?  How can i enter in the password in the command?

---

### Post by Joe_lurker on 2005-11-13
Use the command:
```
sudo -u <username> <command>
```
Replacing <username> with the user you want to run as and <command> is the program to run.
You will be prompted for YOUR password.

Alternatively you can use the "Run as different user" program under Applications | System Tools.

-Joe

---

### Post by Todd_Z on 2005-11-14
I cant run Zend because i dont have the x server running for it - so how do i give one user permission to another user's home directory?

---


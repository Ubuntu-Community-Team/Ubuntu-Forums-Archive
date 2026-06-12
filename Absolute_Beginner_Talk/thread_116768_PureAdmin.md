---
title: "PureAdmin"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by BooDa on 2006-01-13
Hi all, this is my first post on this server, and I'm a bit of a linux, Ubuntu n00b :razz: 

anyhoooo.
I have installed Pureftpd and have the service running (according to PureAdmin, it gives me a pid #)
However, the Admin program is unable ro retreive any server information, and when I try to manage users, it asks me > "The file containing the login-names for virtual users could not be found. you need this file in order to create and edit ftp-users."
So it offers to create the file, so I let it and then it gives me this:
> "Failed Creation
There was an error trying to make the password file[]
The error reported was: No such file or directory"
Does anyone here know where the pw file for this would be, I was thinking of just creating the Dir and seeing if that works.

Thanks in advance
Cheers!

---

### Post by Sef on 2006-01-13
When you are installing it, have you change to the directory that you are installing it from?  

Example:

```
sef@happy:~$ cd ~/pureftpd
```  then you should be here then:

```
sef@happy:~/Desktop$  
```

---


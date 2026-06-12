---
title: "Login inn as root from difrent computer FROM FTP APP"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by pingopongo on 2007-06-04
Hi i hawe installed Ubuntu 6.10

and i want to log in from my other computer thats tunning on win xp 
IM usinf FlashFXP as my ftp app


do i nead to install somting to get this to work ?
i want to log in as root 


and i hawe read all posts here on loging inn as root .. but i still chant manage to log inn to my Ubuntu 6.10
from my oter computer

Pleas Help if enyone chan .

:KS

---

### Post by mattmole on 2007-06-04
Hi,

FTP server is a pretty insecure service to run on your machine. I have not used FTP on any of my machines. I have installed ssh (openssh-server I think is the package) on the machine I wish to connect to. 

I can then connect from another computer with all details of the connection encrypted. To copy files between machines I would use scp (secure copy. scp file_to_copy user_to_connect_as:machine_name_to_copy_to:/path/to/copied_file_name)

Also, you could use sftp, secure sftp, which I think operates via SSH.

Also, why do you need to connect as root? Can you not do whatever you need as a normal user? Copy the files or whatever to a place with normal user permissions, and then connect via SSH and copy things to the root area?

If possible I would not connect directly as root. I would do as I have said and the log in as normal user, and then change to root. In this way any hacker has to hack your normal user account, and THEN hack your root account.

Mattmole :o)

---


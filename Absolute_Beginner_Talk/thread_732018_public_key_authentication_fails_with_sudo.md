---
title: "public key authentication fails with sudo"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by medha on 2008-03-22
I set up the public key using:
Client:
 ssh-keygen -q -f ~/.ssh/id_rsa -t rsa
 scp ~/.ssh/id_rsa.pub server
Server: 
 cat ~/id_rsa.pub >> ~/.ssh/authorized_keys

now, if I do ssh server, it works, probably since it checks for user@client in the authorized keys, but for sudo ssh server, it asks for the password, because it checks for the user root@client for authentication.

How  do I work around this problem? I tried creating the keys as sudo, that didnt work either. 

Thanks!

---

### Post by kevdog on 2008-03-22
Can you be more specific what you are trying to do?  You can specify a login name with the -l switch, for example

ssh -l JoeBlow 

or you can do the following

ssh JoeBlow@server_name

---

### Post by medha on 2008-03-22
It worked! I created the dsa public key with sudo, there were problems with rsa.

---


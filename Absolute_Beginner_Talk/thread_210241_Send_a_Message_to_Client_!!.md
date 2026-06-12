---
title: "Send a Message to Client !!"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by widjaja31 on 2006-07-06
Hi all....
I have one server computer and 3 client computer with ubuntu dapper os inside them. one thing that i want to ask is how to send a message ( or something ) from Server to my client so my client can execute one script that i already prepare in their local drive. 

Thanx Before
Ronny

---

### Post by IYY on 2006-07-06
If you have SSH installed:

```
ssh -l myusername server.ip.address commandname
```

You will need to enter a password. If this is not convinient:

>      ssh implements the RSA authentication protocol automatically.  The user
     creates his/her RSA key pair by running ssh-keygen(1).  This stores the
     private key in $HOME/.ssh/identity and stores the public key in
     $HOME/.ssh/identity.pub in the user's home directory.  The user should
     then copy the identity.pub to $HOME/.ssh/authorized_keys in his/her home
     directory on the remote machine (the authorized_keys file corresponds to
     the conventional $HOME/.rhosts file, and has one key per line, though the
     lines can be very long).  After this, the user can log in without giving
     the password.


---

### Post by widjaja31 on 2006-07-07
how can i configure client to know that if they got a message from server, they have to execute one script in their local harddisk ?

thanx be4
Ronny

---


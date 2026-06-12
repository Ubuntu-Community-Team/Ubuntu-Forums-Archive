---
title: "samba tdb_fetch installation error"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by bunnynuts on 2006-07-25
While installing samba on a Dell Dimension 8200 I receive the following error message:

TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0

I've reinstalled Ubuntu (Dapper Drake) twice and received the message each time.

I've updated/upgraded the repositories and it hasn't made a difference.  Additionally, when attempting to run the smbclient -L command it returns with an unknown command error.

I can see the network from other terminals but can not connect.  

Any ideas/help will be greatly appreciated.

Thanks

---

### Post by halfvolle melk on 2006-07-25
How are you trying to install it?
sudo apt-get install samba? Check out this link, bottom of the page:
[http://64.233.183.104/search?q=cache:Rs5WC1lsQYQJ:docs.hp.com/en/B8725-90102/ch01s05.html+account_policy_get:+tdb_fetch_uint32+failed+for+field+1&hl=en&ct=clnk&cd=3&ie=UTF-8](http://64.233.183.104/search?q=cache:Rs5WC1lsQYQJ:docs.hp.com/en/B8725-90102/ch01s05.html+account_policy_get:+tdb_fetch_uint32+failed+for+field+1&hl=en&ct=clnk&cd=3&ie=UTF-8)
Maybe it's harmless. Did you check if it worked?

---

### Post by bunnynuts on 2006-07-25
Thank you for the help.  
I'm working from command line and so I used the "sudo ap-get install samba" command to install it.  The error message only appeared during the initial installation process and not when I attempted to add a user.  I have tried to access the server from a couple different machines, both display the share in the workgroup computers.  When I attempt to connect I'm immediately given a "you don't have permission" error message. 
I have successfully set up this type of network at home but am not sure why it isn't working now.

---

### Post by halfvolle melk on 2006-07-26
Take a look at the logs in /var/log/samba/. It may show some obvious error.

---

### Post by bunnynuts on 2006-07-26
I ended up reinstalling ubuntu, I reinstalled the samba server(received same error message) and changed the physical arrangement of my network and it is now working. I believe your first post was correct, the error message was benign...which motivated me to continue looking elsewhere for the problem.

Thank you for your time

---


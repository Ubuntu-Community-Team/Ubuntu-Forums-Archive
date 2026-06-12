---
title: "error installing programs"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by paul mcmillan on 2006-11-28
I just updated from dapper to edgy. I am having a problem installing new programs. "  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i tried opening a terminal and running the script ,, but then it says i must be a superuser. 

thanks for help in advance

Paul

---

### Post by qamelian on 2006-11-28
> **paul mcmillan said:**
> I just updated from dapper to edgy. I am having a problem installing new programs. "  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i tried opening a terminal and running the script ,, but then it says i must be a superuser. 

thanks for help in advance

Paul

If you are logged in as the first user you created when you installed Ubuntu, you can get superuser priveleges by using the sudo command. In this case, ```
sudo dpkg --configure -a
```
When you are prompted for a password, just provide the password for your own user account.

---

### Post by paul mcmillan on 2006-11-28
okay got that thanks. now the terminal is running flashplugin,, hanging on the downloading line. i tried installing the flash plugin before and i hanged and crashed also. how can i blow that out of the system

tks

Paul

---


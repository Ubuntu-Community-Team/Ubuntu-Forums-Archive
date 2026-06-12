---
title: "Can't login as admin.  SU not accepting my pwd"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Booter on 2007-03-11
I'm new to linux and just installed Ubuntu and am loving it. I'm trying to install java and need to login as administrator but the 'su' command is not accepting my password (the pwd I set for my userID).  

On install the only time I was asking to set a password was for my userID but never for an admin password.  Is there a default or someway to change this? Did I do something wrong during install?

Thanks so much in advance for any help.

---

### Post by 454redhawk on 2007-03-11
> **Booter said:**
> I'm new to linux and just installed Ubuntu and am loving it. I'm trying to install java and need to login as administrator but the 'su' command is not accepting my password (the pwd I set for my userID).  

On install the only time I was asking to set a password was for my userID but never for an admin password.  Is there a default or someway to change this? Did I do something wrong during install?

Thanks so much in advance for any help.

Ubuntu uses sudo. There is no root account to login to.

type sudo and then your command

sudo command

---

### Post by lamalex on 2007-03-11
you never enabled root acount. do this
```
sudo su
``` enter your account password, the one you use to log on.
```
passwd
``` now type in what you want your root password to be.

---

### Post by lamalex on 2007-03-11
> **454redhawk said:**
> Ubuntu uses sudo. There is no root account to login to.

type sudo and then your command

sudo command

this is incorrect. root account is not enabled by default but not enabling it is a big security hazard. sudo is a way to use root access by switching to root account for just that command.

---

### Post by 454redhawk on 2007-03-11
> **Iamalex said:**
> this is incorrect. root account is not enabled by default but not enabling it is a big security hazard. sudo is a way to use root access by switching to root account for just that command.

Maybe you did not read the OP post?

Thats EXACTLY what he wants and needs to do.

RIF (reading is fundamental)

---

### Post by Booter on 2007-03-11
Thank you all for the quick and helpful replies.  That was pretty straight forward and worked perfectly. 

After typing 'sudo su' and entering my password (had to use my user pwd), when I run 'sudo su' again it logins into root without asking for a password.  Is that okay (ie, safe)?  Also, how do I change the password later on?

Running 'su' by itself still doesn't work; it rejects the password I entered under 'sudo su'

Thanks again for your help.  I very much appreciate it.

---

### Post by 454redhawk on 2007-03-11
> **Booter said:**
> Thank you all for the quick and helpful replies.  That was pretty straight forward and worked perfectly. 

After typing 'sudo su' and entering my password (had to use my user pwd), when I run 'sudo su' again it logins into root without asking for a password.  Is that okay (ie, safe)?  Also, how do I change the password later on?

Running 'su' by itself still doesn't work; it rejects the password I entered under 'sudo su'

Thanks again for your help.  I very much appreciate it.

Please reread my post or have a look at the wiki.
su is not used in ubuntu. use sudo and the command you want to run.
**Enabling the root account is NOT RECOMMENED!**

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Booter on 2007-03-11
454Redhawk, thanks for the help and the link to the wiki.  It makes a lot more sense now and I went ahead and disabled the root account.

---


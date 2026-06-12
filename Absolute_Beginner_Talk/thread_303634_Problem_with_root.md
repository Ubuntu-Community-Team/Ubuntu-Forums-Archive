---
title: "Problem with root"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by henrywm on 2006-11-20
I cannot access my root permissions. The password that I entered for root when I installed Ubuntu is not valid. How do I fix this?

---

### Post by bulldog on 2006-11-20
Can you login in your Ubuntu?
If I'm not mistaken you didn't set a root password by installing Ubuntu,just a user password to login.

This same password gives you root permissions when you use sudo before a command.

---

### Post by henrywm on 2006-11-20
I can log in. I do not remember giving two passwords, but apparently there are two.
I first discovered the problem when I tried to edit the sources.list file and was denied permission. I checked the "Users and Groups" dialog and noticed that the root password is one character longer than my account's password.

---

### Post by henrywm on 2006-11-20
I am certain that I did not enter two passwords when installing. I do not know how this happened.
The Guest account that I setup has also vanished.

---

### Post by bulldog on 2006-11-20
Well I can tell you,you have to give just one password when you installed Ubuntu,or you have a very special edititon.:D 

To edit your sources list try```
gksudo gedit /etc/apt/sources.list
```

Or try in your terminal```
sudo -s
``` and see if you become root.
Type exit to leave your root account!

---

### Post by jd65pl on 2006-11-20
Hey, have a look at this it should help you out

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by henrywm on 2006-11-20
"sudo -s" put me in root, but why are there different passwords for my account (first user) and root in the "Users & Groups" dialog. There certainly seem to be two different passwords, because the root password is one character longer in that dialog box.

Second, why does he Guest account vanish?

---

### Post by henrywm on 2006-11-20
This is strange. I checked Users and Groups again. The password field shows an extra character in the password fields for both my account and root, and yet my password works for my account. I do not need the extra character (whatever it is) to log in to my personal account.

---

### Post by henrywm on 2006-11-20
How do I set the permissions to allow me to edit sources.list from the GUI with "Text Editor." It will let me open the file and type the changes, but it will not let me save the changes due to permission restrictions.

---

### Post by bulldog on 2006-11-20
You have to use ```
gksudo nautilus
```
So you can browse to the file you want to alter,but take a good advice,**make always a copy before altering anything**

Succes.

---

### Post by Puntal on 2006-11-20
Hi.

I HAve the same problem.

Went to add a directory,but it tells me i need to be logged in as root.
Now,had a look in the users and groups,and there is a user called "root" there.
But when i try to change password,it wont let me,try to login with user "root" and password that i assigned for installation user,still dowesnt work.

Question ismhow do i login as root instead of my created admin user?

Thanks

---

### Post by melancholeric on 2006-11-20
You don't login as root. You use sudo. Enabling logging in as root is possible but not exactly recommended.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jd65pl on 2006-11-21
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

There shouldn't be much requirement to log in as "root" all tasks can be performed using 'sudo' or 'gksudo'

---


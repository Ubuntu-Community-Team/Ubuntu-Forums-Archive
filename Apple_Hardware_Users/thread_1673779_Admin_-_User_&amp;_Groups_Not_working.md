---
title: "Admin - User &amp; Groups Not working"
date: 2011-01-22
forum: Apple Hardware Users
---

### Post by BlastXng on 2011-01-22
After finally getting Ubuntu 10.10 PPC up and working on my Mac Cube with low capability graphics, I noticed that when I try to run the "User and Groups" from the Administration menu, the program looks like it is starting but then never actually displays.. It shows up at the bottom of the running programs bar and then disappears. 

Well after having to completely re-install Ubuntu PPC 10.10 and installing all of the updates, User and group Administration still isn't working.. 

Does anyone know of a bug with this application on 10.10 PPC?

Does anyone know of another app that would let me add my wife to my G4 Cube so she could use it?

Thanks

---

### Post by TODDMAN on 2011-01-31
Same problem here on my iMac PPC :(

---

### Post by TODDMAN on 2011-02-10
Has anybody successfully been able to create a new user on a powerpc?
 
Thanks,

---

### Post by linuxopjemac on 2011-02-11
very simple, in a terminal:
```
sudo useradd "username"
```
where "username" is the new user name

---

### Post by TODDMAN on 2011-02-11
> **linuxopjemac said:**
> very simple, in a terminal:
```
sudo useradd "username"
```
where "username" is the new user name
 
So how do you add a password?
 
Thanks!

---

### Post by linuxopjemac on 2011-02-11
Can you explain what happens? It should be straightforward.

---

### Post by TODDMAN on 2011-02-11
> **linuxopjemac said:**
> Can you explain what happens? It should be straightforward.
don't you need to make a password after you make a new user account?

---

### Post by linuxopjemac on 2011-02-11
try:

```
sudo adduser "username"
```

---

### Post by linuxopjemac on 2011-02-11
deluser deletes the user account

---

### Post by TODDMAN on 2011-02-11
> **linuxopjemac said:**
> try:

```
sudo adduser "username"
```
Still need a password to login to new user.

---

### Post by linuxopjemac on 2011-02-12
```
jeroen@jeroen-mint ~ $ sudo adduser test
[sudo] password for jeroen: 
Adding user `test' ...
Adding new group `test' (1002) ...
Adding new user `test' (1002) with group `test' ...
Creating home directory `/home/test' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for test
Enter the new value, or press ENTER for the default
	Full Name []: test
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] 
```

At the point of new UNIX password you give the password for the new user...You have to do it twice. At the first password prompt you give your own password. You need to be in the /etc/sudoers list for that. If you don't have that you do it from root. Login as root:
```
su
```
hit enter and give the root password
then
```
adduser 'newuser'
```
and follow what's asked.

---

### Post by TODDMAN on 2011-02-12
Thanks linuxopjemac that work :)

---


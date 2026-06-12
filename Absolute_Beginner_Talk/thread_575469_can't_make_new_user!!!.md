---
title: "can't make new user!!!"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-10-14
I have created several users for this machine... all using GUI. it worked well enouhg.

However i tried to make a new user and it will not let me log in to that account.

I get a msg to the effect of

```
userhome/.dmrc is being ignored..
```..


then when I hit enter I get sg about

```
last session only lasted 10 seconds....
```

what gives?

robi

---

### Post by wormser on 2007-10-14
It looks like your permissions for .dmrc are wrong.  Try the following.

```
ls -l /home/username/.dmrc
```

> It should look like this:
-rw------- 1 username username 26 2007-04-19 16:10 .dmrc

If the permission part is different then:

```
sudo chmod 600 /home/username/.dmrc
```
Then try to log in.

---

### Post by beanco on 2007-10-14
about to give it a try,
tahnks for the info

happen to know of any permissions for morons tutorials that I could read through?

they still confuse me.

I wanted to set up my daughter's account and add myself to her group, doing so would give me full access to her account, right?

robi

---

### Post by beanco on 2007-10-14
got this

```
rob@rob-desktop:~$ ls -l /home/ancsi/.dmrc
ls: /home/ancsi/.dmrc: No such file or directory

```

---

### Post by wormser on 2007-10-14
That is strange it is not there.  You might want to double check by cd into that home directory and do an ls -la.  You could always create the file and give it the correct user, group and permissions.  The following quote has everything in my .dmrc file.

> [Desktop]
Session=default

---

### Post by beanco on 2007-10-14
[HTML]> **wormser said:**
> That is strange it is not there.  You might want to double check by cd into that home directory and do an ls -la. [/HTML]


got this

```
rob@rob-desktop:/home$ ls -la
total 32
drwxr-xr-x  8 root root  4096 2007-10-02 18:11 .
drwxr-xr-x 22 root root  4096 2007-10-01 19:54 ..
drwxr-xr-x  2 1002  1005 4096 2007-10-02 18:11 ancsi
drwxr-xr-x 28 aron aron  4096 2007-10-14 10:40 aron
drwxr-xr-x  2 evi  evi   4096 2007-10-02 18:11 evi
drwxr-xr-x  9 1002 laci  4096 2007-09-28 19:54 laci
drwxr-xr-x 34 rob  rob   4096 2007-10-14 10:12 rob
drwxr-xr-x  9 aron zsolt 4096 2007-09-28 19:55 zsolt
rob@rob-desktop:/home$ 

```

```
 You could always create the file and give it the correct user, group and permissions.  The following quote has everything in my .dmrc file.
```

sounds good, but i do not know how to do it!!???!??

robi

---

### Post by wormser on 2007-10-14
I just created a test user and did ls -la.  

> drwxr-xr-x 2 testuser testuser  152 2007-10-14 02:28 .
drwxr-xr-x 4 root     root      104 2007-10-14 02:28 ..
-rw-r--r-- 1 testuser testuser  220 2007-10-14 02:28 .bash_logout
-rw-r--r-- 1 testuser testuser 2298 2007-10-14 02:28 .bashrc
lrwxrwxrwx 1 testuser testuser   26 2007-10-14 02:28 Examples -> /usr/share/example-content


Your user does not have the .bash_logout or .bashrc file.  I would try to delete the user and recreate it first.

---

### Post by beanco on 2007-10-14
ok I will delete here and then recreate her.

i would like ot learn how to do it from teh command line. i do not like this gui user/group thing...

so what are the commands for creating a user?

delete is sudo deluser right?


and thanks!!!


robi

---

### Post by beanco on 2007-10-14
bump

---

### Post by beanco on 2007-10-14
hey, messing round, trying to deluser, adduser, etc

and then I ran

```
rob@rob-desktop:~$ ls -l /home/ancsi/.dmrc
```

and got this

```

ls: /home/ancsi/.dmrc: Permission denied

```

so i tried and got this
```

rob@rob-desktop:~$ ls -l /home/ancsi/.dmrc
```

what's going on here?

thanks for the help, BTW!!!!

---


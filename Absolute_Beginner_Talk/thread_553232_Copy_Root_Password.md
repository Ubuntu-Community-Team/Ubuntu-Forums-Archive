---
title: "Copy Root Password"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-09-17
Just wonder if I can copy a password (assume that it's coded and stored in a file) to another user account if I have sudo access no password.

---

### Post by raul_ on 2007-09-17
I don't get it. Could you explain it better?

---

### Post by Jonne on 2007-09-17
I think you want the /etc/shadow file. Although I wouldn't touch that without doing some research on how it works...

---

### Post by bodhi.zazen on 2007-09-17
o.O

What ???

---

### Post by kellemes on 2007-09-17
On Ubuntu there is no root password set to begin with.

---

### Post by lakris61 on 2007-09-17
Yes, You can copy the coded password from one user and put it in the other users location for the password... 

lakris@ubuntu:~$ sudo su -
Password:
root@ubuntu:~# adduser qwerty
Adding user `qwerty' ...
Adding new group `qwerty' (1009) ...
Adding new user `qwerty' (1002) with group `qwerty' ...
Creating home directory `/home/qwerty' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: (I entered qwerty)
Retype new UNIX password: (twice!)
passwd: password updated successfully
Changing the user information for qwerty
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [y/N] y
root@ubuntu:~# adduser asdfg
Adding user `asdfg' ...
Adding new group `asdfg' (1010) ...
Adding new user `asdfg' (1004) with group `asdfg' ...
Creating home directory `/home/asdfg' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: (I entered asdfg)
Retype new UNIX password: (and again)
passwd: password updated successfully
Changing the user information for asdfg
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [y/N] y
root@ubuntu:~# vi /etc/shadow


And change the lines so that asdfg has the same as qwerty...
qwerty:$1$h0q4qCWR$xdYaT4Lzuq3k.XwtLBDWS/:13773:0:99999:7:::
asdfg:$1$h0q4qCWR$xdYaT4Lzuq3k.XwtLBDWS/:13773:0:99999:7:::
**************
and then test it...
root@ubuntu:~# logout
lakris@ubuntu:~$ su - qwerty
Password:  (I entered qwerty)
qwerty@ubuntu:~$ logout
lakris@ubuntu:~$ su - asdfg
Password: (I entered qwerty)
asdfg@ubuntu:~$ logout

But why would You want to do that? Use passwd and change it, because You are root, right?

---

### Post by aspen_dv on 2007-09-24
Thanks Lakris,
The reason for this is one user forgot the root password and I have sudo access. Instead of reset the password, I would like to make his current user password to be root as well (he owns that server anyway).

---


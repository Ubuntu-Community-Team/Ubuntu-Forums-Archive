---
title: "vsftpd"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-11-09
what parameter should I change in in the .conf file in order to be able to allow only one user( with its correspondant pswd)  and to define a directory for him?


thx


J

---

### Post by johnnyw on 2007-11-12
can someone help me please?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
umm i am not shur what you mean

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
only one user on the system
?
have you ever had multiple users

---

### Post by johnnyw on 2007-11-14
the idea is to pass a friend some files

---

### Post by ruibernardo on 2007-11-14
Hi johnnyw,

starting from the default /etc/vsftpd.conf, the one you get when you install vsftpd, disabel anonymous login, enable local users and chroot them:
```
# disable anonymous login (optional)
anonymous_enable=NO

# enable local users (uncomment it)
local_enable=YES

# enable local users to write (optional, uncomment it)
write_enable=YES

# chroot local users so they can't leave their home directory (uncomment it)
# NOTE: if you don't use this option, users can "walkout" from their home 
# directory or local root you set with local_root=.
chroot_local_user=YES

```The following options aren't on the default /etc/vsftpd.conf, so add them in the end of the file.

Enable the option userlist_enable to have a file with the list of users that can login. If a user tries to login and isn't on the list, he will get an error even before he types his password. To use userlist_enable, disable the userlist_deny, because vsftpd uses the user list to deny users by default.
```
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd/allowed_users

```Create the directory /etc/vsftpd. In the file /etc/vsftpd/allowed_users add the username of the users that can login.

Now to put the user on a particular directory, set a directory where vsftpd can look for special options for each users. For this example it will be /etc/vsftpd/. 
```
user_config_dir=/etc/vsftpd/
```Inside that directory create a file for each user that you want to have "special" options.
```
# /etc/vsftpd/mary
# chroot her in her mp3 directory:
local_root=/home/mary/Desktop/mp3

```Hope this works for you.

---


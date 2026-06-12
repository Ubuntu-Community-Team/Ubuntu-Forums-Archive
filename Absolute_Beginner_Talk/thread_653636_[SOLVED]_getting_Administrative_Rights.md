---
title: "[SOLVED] getting Administrative Rights"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-12-30
yesterday when i read that the account you use to surf the net should not have Administrative Rights. i went to system>administration>user&group. then selecting my account and pressing edit button i go to the second tab and unchecked the system administrator column. 
and didn't think of what i have done
today when i  logged in my account to most of the items in the system>administration where gown.
and i have not given system administrator right to another account.
now i have 2 account one which used to be administrator and now just a user, and second account with no administrator rights.
now again i want to make my first account which i created at the time of installation, the  administrator.
please help.

---

### Post by hyper_ch on 2007-12-30
(1) boot into recovery mode

(2) run this command:

```

useradd -G admin USER

```

USER = your user name!

maybe you also have to run:

```

useradd -G adm USER

```

I just checked my usergroups and I am member of those additional ones:

adm, admin, audio, cdrom, dialout, dip, floppy, lpadmin, netdev, plugdev, powerdev, scanner, video

---

### Post by rahul_bhise on 2007-12-30
i logged in the recovery mode auseradd -G admin USERnd gave the root password then i did
useradd -G admin USER
but it said the "USER" already exist
so i did
useradd -G admin NEWUSER
then gave it a password by
passwd NEWUSER
then restarted and then tried to login with NEWUSER. after entering password it said
```
your home directory is listed as /home/NEWUSER but it does not exist
. do you want to log in with the /(root) directory as your home directory it is unlikely anything will work 
unless you use a failsafe session
```
i clicked on yes then another message was shown
```
users $home/.dmrc file is being ignored. this prevents the default session
 and language from being saved file should be owned by user and have 644 permission
 users $home directory must be owned by user and not writable by other user
```.
i again clicked ok. the third message showed
```
your session only lasted less than 10 seconds. if you have not logged out yourself 
this could mean that there is some installation problem or you maybe out of disk space. 
try logging with one of the fail safe session to see if you can fix the problem
```

---

### Post by rahul_bhise on 2007-12-30
ok i solved it what i did was
```
adduser USER admin
```
in the recovery mode after giving a root password
thanks to [psychocats]("http://www.psychocats.net/ubuntu/sudo")

---

### Post by John Ivens on 2008-04-07
OK But how do I add the password whilst I'm in the recovery mode; I've added USER as you describe.

I am a very new user - about 3 hours in, so I apologise if this is a bit basic.
John Ivens

---

### Post by lswest on 2008-04-07
USER is meant to be your actual username.

---


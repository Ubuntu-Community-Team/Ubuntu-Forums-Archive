---
title: "list users"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by mixerman on 2007-01-15
I'm new to completely new to this.  I installed fine, logged on as oem the then rebooted to create a new username.  I must not have remembered correctly how I typed my new user name.  Now I cannot login.  I went into the recovery mode by pressing the "esc" key and tried to change the password for my username, but it said there was no such user name.  Is there a way to get a list of user names so I can log in?  Or a way to start over with user names?

Thanks,

Chris

---

### Post by diepruis on 2007-01-15
Try
```

cat /etc/passwd

```
The user names are in the first column. Before the first ':'.

---

### Post by CT Husky on 2007-01-15
One other thing I noticed: all usernames must start with a lowercase letter, so be sure you are not capitalizing.

---

### Post by taurus on 2007-01-15
Or look in the /home directory.

```
ls -la /home
```

---

### Post by mixerman on 2007-01-15
Well, I never found anything that looked even close to what I thought I had put in as user name.  I did the whole "oem-config-prepare", and started over.  I created a new username (in lower case) and when I logged on it all worked fine.

Thanks for all the quick help!

---


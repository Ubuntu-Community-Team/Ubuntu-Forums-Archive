---
title: "passwd"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by [pl]ice on 2005-07-22
hi, i just installed openssh, but i haven't yet set up makejail, or anyting , so user has standard shell ... so i tried the login, and to my suprise i can see cat /etc/passwd ... don't like that, and i know it uses shadow. it's presmissions are: -rw-r--r--  1 root root

is that correct?

---

### Post by FLeiXiuS on 2005-07-22
[QUOTE='[pl]ice']hi, i just installed openssh, but i haven't yet set up makejail, or anyting , so user has standard shell ... so i tried the login, and to my suprise i can see cat /etc/passwd ... don't like that, and i know it uses shadow. it's presmissions are: -rw-r--r--  1 root root

is that correct?[/QUOTE]

Passwd has to be accessed by all users regardless.  The users hashed password must be available to each user.  One way of enhancing security is by enabling shadow passwords.  If your familiar with the way passwords work, well this adds a SALT hash to the end of the current hash.  Making the password 10X harder to decrypt.

```
sudo shadowconfig on
```

---

### Post by [pl]ice on 2005-07-23
yeh, got shadow on :)
  it just seemed to me that one can pull out v.easily usernames... but yep, will setup jail for ssh.
thanks.

---


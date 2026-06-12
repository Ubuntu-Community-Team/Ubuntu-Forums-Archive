---
title: "&quot;~#&quot; Vs &quot;#&quot;  ???"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jackpetrilli on 2007-12-08
I've given the root user a password, so now I can use the su command in Ubuntu.  However, when I do, I get the # symbol in my terminal, as opposed to the ~# symbol that results if you execute sudo -i.  

Does anyone know what the difference is here?  I'm thinking that with the sudo -i, I remain the user but with superuser privileges, whereas with the former command, I am the root superuser.  Is this correct?

More importantly, are there any differences at all in what I can do under the su command, that I can't with the sudo -i command?

- Jack

---

### Post by NullHead on 2007-12-08
> **jackpetrilli said:**
> I've given the root user a password, so now I can use the su command in Ubuntu.  However, when I do, I get the # symbol in my terminal, as opposed to the ~# symbol that results if you execute sudo -i.  

Does anyone know what the difference is here?  I'm thinking that with the sudo -i, I remain the user but with superuser privileges, whereas with the former command, I am the root superuser.  Is this correct?

More importantly, are there any differences at all in what I can do under the su command, that I can't with the sudo -i command?

- Jack

All I know about the subject is that when you sudo -i you remain as you're normal user with root privileges and you don't have to type sudo when you do a command.

---

### Post by schauerlich on 2007-12-08
Using sudo, you are a normal user who is allowed to execute commands as root. Using su, you log in as root. Read this for more information: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by spiderbatdad on 2007-12-08
in the latter case ~# you are in your home directory. doing sudo -i attempts to place the current user in his home directory. in either case you are root, only pwd is different.
As outlined in:
```
man sudo
```

---


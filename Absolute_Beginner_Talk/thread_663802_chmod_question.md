---
title: "chmod question"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by lex1 on 2008-01-10
just a basic permissions question  i must chmod 600 this 



 msmtp: /home/tim/.msmtprc:

is the correct line as root (see below)   

chmod 600 .msmtprc:msmtprc



lex1

---

### Post by dgray_from_dc on 2008-01-10
You should only have to type

```
sudo chmod 600 .msmtprc
```

Provided you're in the /home/tim directory.

---

### Post by lex1 on 2008-01-10
thanks its easy when you remember:popcorn:

---

### Post by lex1 on 2008-01-10
should i do it as root?

tim@~$ sudo chmod 600 .msmtprc

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password:
tim is not in the sudoers file.  This incident will be reported.

---

### Post by PeterJS on 2008-01-10
Was tim the first account created on the machine when you installed Ubuntu? The default for the installer is to only make the first account an administrator account.

Also you shouldn't need to use sudo to use chmod.

---

### Post by stchman on 2008-01-10
> **lex1 said:**
> just a basic permissions question  i must chmod 600 this 



 msmtp: /home/tim/.msmtprc:

is the correct line as root (see below)   

chmod 600 .msmtprc:msmtprc



lex1

Remember the ~ and the -R.  The ~ stands for the currently logged in users home directory and the -R is recursive into subfolders.

```
chmod -R 600 ~/.msmtprc
```

---


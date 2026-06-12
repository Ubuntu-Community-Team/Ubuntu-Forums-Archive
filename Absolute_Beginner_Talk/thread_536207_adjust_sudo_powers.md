---
title: "adjust sudo powers"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by mgvbstar on 2007-08-27
Hello.  I've been using ubuntu on my laptop for about a year and i love it so I decided to install feisty on my home desktop computer which my entire family uses.  On the desktop, I have multiple user accounts.  I want each user to be able to install new packages (so they must be able to sudo) but I do not want them to be able to change other user's passwords (so they can't sudo passwd).  Is there a way I can do this, or more generally can I control what a user can sudo and what they cant? Thanks.

---

### Post by dreadlord_chris on 2007-08-27
> **mgvbstar said:**
> Hello.  I've been using ubuntu on my laptop for about a year and i love it so I decided to install feisty on my home desktop computer which my entire family uses.  On the desktop, I have multiple user accounts.  I want each user to be able to install new packages (so they must be able to sudo) but I do not want them to be able to change other user's passwords (so they can't sudo passwd).  Is there a way I can do this, or more generally can I control what a user can sudo and what they cant? Thanks.

simple answer: Yes it involves editing the _sudoers_ file
CAVEATS
       The sudoers file should always be edited by the visudo command which locks the file and
       does grammatical checking. It is imperative that sudoers be free of syntax errors since
       sudo will not run with a syntactically incorrect sudoers file.

first you need to RTFM:
```

man sudoers

```
There is alot to read - you should make sure you understand what you are doing...

when you're ready:
```

sudo visudo

```
will start the editor for sudoers...

---

### Post by Zootropo on 2007-08-27
You will have to add something like this to sudoers
myuser ALL=(ALL) NOPASSWD:/usr/bin/aptitude

Take a look at this (spanish):
[Cómo hacer que sudo no nos pida contraseña y otros trucos relacionados ](http://mundogeek.net/archivos/2007/05/14/como-hacer-que-sudo-no-nos-pida-contrasena-y-otros-trucos-relacionados/)

---


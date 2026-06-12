---
title: "password"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by ALPHAVICTOR on 2008-03-12
what are the different password protections offered in ubuntu

---

### Post by Oldsoldier2003 on 2008-03-12
> **ALPHAVICTOR said:**
> what are the different password protections offered in ubuntu

Thats kind of a broad undefined question... What context are you looking at? Logging in, protecting files, what encryption methods are supported?

---

### Post by jan quark on 2008-03-12
can you please specify which password do you mean?
the login passwrd?

---

### Post by bswilson on 2008-03-12
You might want to check out the [Ubuntu Community documentation on security]("https://help.ubuntu.com/community/Security"), specifically the documentation on [strong passwords]("https://help.ubuntu.com/community/StrongPasswords").

---

### Post by ALPHAVICTOR on 2008-03-12
can anybody pls mention all of them

---

### Post by jken146 on 2008-03-12
I don't really understand your question.  Each user has a password that they use to log in.  Root security is handled by [sudo]("https://help.ubuntu.com/community/RootSudo").

What else did you have in mind?

---

### Post by ALPHAVICTOR on 2008-03-12
i want to know is there any provision in linux to lock ur files and folders and any other applications as well

---

### Post by jken146 on 2008-03-12
The permissions system in Linux is such that each user can only edit files in his own home directory.  You can also change permissions on your own files so that no one else can read them.  The exception to this is root, the Super User, who can do anything.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) might help explain things.

---

### Post by jeffus_il on 2008-03-12
Since you say applications, maybe you are interested in "lockdown"
See this link:
[http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)

---

### Post by bswilson on 2008-03-13
> **ALPHAVICTOR said:**
> i want to know is there any provision in linux to lock ur files and folders and any other applications as well

I think we're trying to help you, but your question is ill-formed.  What are you trying to accomplish, exactly?  Setting the file and/or folder permissions will `lock` your files.  You can make them unreadable by other users or groups.  Other folks have replied with links that tell you all about GNU/Linux file and folder permissions.

---


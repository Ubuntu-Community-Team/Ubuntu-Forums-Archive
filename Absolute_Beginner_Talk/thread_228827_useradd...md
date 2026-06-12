---
title: "useradd.."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-08-03
when I try adding users with useradd on the command line it does not create a  default home directory for the new user. Does anyone know what I am doing wrong. It just adds the new user but with no home directory, I dont know what to do.
Here is the syntax that I am using when creating new users:
> 
useradd username
I am logged in as root when doing this.
Then I set the users password using passwd.
everything goes well but when i try logging in with that user it tells me that there is no home directory for the user. I would appreciate any help.

---

### Post by aysiu on 2006-08-03
I'm not sure what *useradd* does, but I think *adduser* generally creates a /home directory. ```
adduser username
```

---

### Post by grim918 on 2006-08-03
oh, your right I forgot that some distros use useradd and others use adduser. Thank you for clearing that up. useradd does work on ubuntu though. It just does not create a /home directory for the user. Thank you very much.

---

### Post by hw-tph on 2006-08-03
useradd is standard across most Linux distributions (and very similar across all modern Unixes) while adduser takes a few different forms. useradd does create a home directory if you tell it to - use the -m switch, and -k to create the default files in the home directory (copied from /etc/skel).

Read useradd(8).

Håkan

---


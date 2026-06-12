---
title: "What is 'valid users=@users' in smb.conf mean?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by mak90 on 2007-03-06
Simple question I'm sure.

But in a samba share like:

[share]

...
..
...
..
...
valid users=@users
write list=@users_rw

What is the @users?

Would that be referring to some system global variable or something? Is it a samba-server user? Is it a Linux system user? Any thoughts?

Thanks a million!

:guitar:

---

### Post by christhemonkey on 2007-03-06
From here:
[http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)
> If a user =  field is given in the smb.conf file for the service and the client has supplied a password, and that password matches (according to the UNIX system's password checking) with one of the usernames from the user = field, the connection is made as the username in the user = line.** If one of the usernames in the user = list begins with a @, that name expands to a list of names in the group of the same name.**


---


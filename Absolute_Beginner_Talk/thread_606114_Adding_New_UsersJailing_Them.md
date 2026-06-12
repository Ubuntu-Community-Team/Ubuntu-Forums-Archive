---
title: "Adding New Users/Jailing Them"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by mattc908 on 2007-11-07
Hey Just wanted to know the command to add a new user than how would I jail that user to a certain directory were they can upload and stuff to their directly, not be able to download but just upload. Or if thats not possible Both. Also for MYSQL whats the command to add a new user there.

---

### Post by ubnewbie2 on 2007-11-08
You control where a user can put files by setting the permissions on the directory/folder. You can do this for individual users, or by setting up a user group, setting the group permissions, and putting the users in that group with no permissions of their own.

Standard permissions are Read, Write, and/or Execute and I believe you can make it write only - give it a try.

---

### Post by mattc908 on 2007-11-08
Alright thanks but, I was looking for the commands, and how to jail them to just one folder.

---

### Post by ubnewbie2 on 2007-11-08
> **mattc908 said:**
> Alright thanks but, I was looking for the commands, and how to jail them to just one folder.


try

```
man chmod
man chown
man chgrp
```

That will explain how to use the basic commands.    They will be able to see any file/directory for which they have read permission, save or alter files anywhere they have write permission, and be able to run anything for which they have execute permission.

just set the permissions in your system's directory structure, so you achieve what you desire.

One simple example, is to make them the owner of the desired directory, and no others in your system, then grant r/w/x permission for owners to that directory.

Then they will only be able to write to that directory (and any other directories in your system with global r/w permissions)

---

### Post by mattc908 on 2007-11-08
Muchos Gracias, thats what I was looking for, much appreciated.

---

### Post by hyper_ch on 2007-11-09
well, I assume you are operating some kind of server. A secure and simple way (IMHO) would be giving them SSH access and you MySecureShell to jail them in their homes.

With MySecureShell they can use SCP/SFTP to connect and up/download stuff from their home folder.

---


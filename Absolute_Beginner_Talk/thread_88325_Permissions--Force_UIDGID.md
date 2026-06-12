---
title: "Permissions--Force UID/GID"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by duminas on 2005-11-10
My www folder (for Apache), specifically, /media/www, has files uploaded to it by two users, both of which are in a group called **ftpaccess**; the second user is my FTP account, and the first is my standard user.

How can I make it so that any file put in the www folder (by either user) is automatically owned by the FTP account user and the ftpaccess group, if such is possible? The permissions on the folder at present are 0775, but this doesn't play too nicely when my regular user creates a file in there, as he becomes the owner, and his primary group becomes the owning group (hence my ftp user has no write to the file).

I heard about SGID (2---) having the use of automatically setting the group id on any file within the folder to that of the folder's owning group, but can the same be done for user as well?

Thanks much.

---

### Post by Kyral on 2005-11-10
Yah...I think its SUID....not too sure...

---

### Post by banadushi on 2005-11-10
```

# chgrp ftpaccess /media/www
# chmod g+S /media/www

```
Files will then be owned by the user that created them and the group will be forced to 'ftpaccess'.  The permissions of the file is determined by the umask of the user.  By default files will be created with the permissions of 0644.  You will need to change the umask for users in the ftpaccess group so that they will be creating files which are also group writeable.

Depending on the ftp server you are using you may be able to force the umask server wide or will have to do it on a per user basis.  The umask you will want to set it as is 0002.

Have a good one

Jason

---

### Post by duminas on 2005-11-10
Awesome, thanks guys.

@Kyral:
SUID doesn't force user, sadly. :\

One more thing--is there any reason why my standard user cannot change mode on  things within this directory (all which ftp:ftpaccess owns), where he's the "administrator" Ubuntu created? With sudo, I can, but not as myself.

I'd think his being a member of the owning group and the mode on the parent folder being 2775 (775 everywhere within) would give him the ability to change mode, though this might be a built-in security measure, I guess.

This problem's not too big, since I can sudo around it, but I'd like to know the reason behind it at the least.

---


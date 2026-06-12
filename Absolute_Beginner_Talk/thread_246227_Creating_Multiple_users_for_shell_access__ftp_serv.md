---
title: "Creating Multiple users for shell access / ftp server"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by underdog on 2006-08-29
Hi,
I've been using ubuntu for a little bit, and I want to offer shell accounts to a few of my friends. I don't really know much about adding users / setting permissions for them. I just want them to have a home directory, not be able to screw anything up, etc.

Also, what ftp server is best in everyone's opinion for offering: a personal directory for each user, as well as access to one common directory with read-only access.

This will be probably 3-5 users at most.

Thanks

---

### Post by TFX360 on 2006-08-29
> **underdog said:**
> Hi,
I've been using ubuntu for a little bit, and I want to offer shell accounts to a few of my friends. I don't really know much about adding users / setting permissions for them. I just want them to have a home directory, not be able to screw anything up, etc.

Also, what ftp server is best in everyone's opinion for offering: a personal directory for each user, as well as access to one common directory with read-only access.

This will be probably 3-5 users at most.

Thanks

Dear underdog,

See [here the useradd]("http://linux.about.com/od/commands/l/blcmdl8_useradd.htm") command

I really don't know what the best FTP server is for linux/Ubuntu.  I'll keep an eye on this thread too.

Mmm, check [Proftpd here]("http://www.ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server")


Kind regards,


TFX

---

### Post by mlind on 2006-08-29
For adding new users you can use System > Administration > Users and Groups
in Ubuntu (GNOME) desktop. To add users from command line, use **adduser**. Home directory should be create automatically for new users.

On default setup, home directories are "world readable", but you can change that by doing
```

sudo dpkg-reconfigure adduser

```

You restrict user's permissions by using groups.

---


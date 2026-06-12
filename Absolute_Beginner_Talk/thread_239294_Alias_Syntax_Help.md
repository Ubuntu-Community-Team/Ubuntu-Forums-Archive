---
title: "Alias Syntax Help"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-08-19
I'm trying to create an alias for the command to mount my Truecrypt directory.  The command is 

truecrypt /home/backup /mnt/ --mount-options 'umask=000,uid=1000,gid=100'

(the bit on the end is the only way I know to set permissions to be able to write to the mount)

I tried alias mount='truecrypt /home/backup /mnt/ --mount-options 'umask=000,uid=1000,gid=100'', but it didn't like that.

What's the correct syntax to alias a command that already has single quotes and equal signs in it?

Thanks

---

### Post by scxtt on 2006-08-19
try:

alias mount="truecrypt /home/backup /mnt/ --mount-options \'umask=000,uid=1000,gid=100\'"

---

### Post by uzd4ce on 2006-08-19
Cool, looks like that worked.  

Thanks

---


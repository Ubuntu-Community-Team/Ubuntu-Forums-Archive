---
title: "File access help"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by mlalich on 2006-10-20
I'm trying to enable iptables, but the file I need to edit is owned by root. My username is darkmatter, how am I able to edit and save the file as darkmatter? Is there a way to give myself full rights and permissions?

Thanks in advance!

---

### Post by Kateikyoushi on 2006-10-20
Use the sudo or gksudo command.

```
sudo nano path_to_filename
```

You can read more here, [Rootsudo documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by kingmonkey on 2006-10-20
Type in terminal

sudo nano whichever.file.u.want.to.edit

for more information google sudo

---

### Post by Ben Sprinkle on 2006-10-20
```

sudo su
* Then your command
```

---

### Post by bsussman on 2006-10-20
sudo is the generally accepted safe way of doing 'root things' in the ubuntu community.  I consider it an important contribution to the whole 'science' of how to administer systems!

Using sudo keeps your audit trail clean and complete and is a very good habit, even if this is only your own desktop, you live alone and never connect to the net :)

You really do not want the standard user(s) to have unlimited access to system files - you want (trusted) users to be able to temporarily acquire the power necessary to make adjustments, install, etc.

Don't change the ownership or permissions on this file.  There are security and system reliability issues with changing metadata on system files.

---


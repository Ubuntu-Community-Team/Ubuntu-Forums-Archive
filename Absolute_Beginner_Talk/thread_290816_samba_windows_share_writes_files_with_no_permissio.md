---
title: "samba windows share writes files with no permission"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-11-01
I have a shared drive, which my Windows XP machine writes files to.
But these files are always locked, there group is set to "nobody"?
Now I can easly sudo chown the files, but how can I set samba/mount/permissions so that the files are written normal?

---

### Post by Joe_CoT on 2006-11-01
In that share's section in your smb.conf
```
sudo gedit /etc/samba/smb.conf
```

you can set the user or group for everyone who accesses the files through samba
```

force user = your-user
force group = your-group
```

and/or you can use umask to set the permissions for new files

```

writable = yes
create mask = 0777
directory mask = 0777

```

The masks work like normal chmod permissions

---

### Post by IanVaughan on 2006-11-02
Wicked! Worked a treat.
Just thought I'd add that samba of course has to be restarted, just for completeness for anyone else reading...
```
sudo /etc/init.d/samba restart
```

---


---
title: "Permissions problem"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2008-03-25
when i login i get this little msg
> User's $home/.dmrc file is being ignored. this prevent the default sessions and lanugage form being saved. File should be owned by user and have 644 permissions. user's $home directory must be owned by user and not writable by other users. i couldn't find .dmrc in my home dir, anyone know what i should do?

---

### Post by smartboyathome on 2008-03-25
Press control-alt-f1, log in as your user, then type sudo chown yourusername ~/.dmrc. See if that helps.

---

### Post by scragar on 2008-03-25
try:
```
gedit ~/.dmrc
```
(replace gedit with nano if you need to use the command line to do it)then paste in:
```


[Desktop]
Session=default
```
and finish up with correcting the perms:
```
chmod 644 ~/.dmrc
```

---

### Post by cerealtx on 2008-03-25
tried both, still getting the error

---


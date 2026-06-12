---
title: "Log in error"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by G_force on 2007-02-24
Every time i log in to ubuntu it get this message

" Users $HOME/.dmrc file is being ignored. This prevents the default
session and language to be saved. File should be owned by user and
have 644 permissions. Users $HOME directory must be owned by the 
user and not writable by others."

this my have happened when i changed permissions to delete a file.

Anyone know how to change it back

Cheers

(Thanks in Advance)

---

### Post by taurus on 2007-02-24
Boot into recovery mode from GRUB menu and run

```
chown -R **gforce**:**gforce** /home/**gforce**
chmod 644 /home/**gforce**/.dmrc
```
Assuming **gforce** is your login name.

Then, reboot and see if you can log in without any error message about $HOME/.dmrc.

```
shutdown -r now
```

---

### Post by G_force on 2007-02-24
Hi again

I tried that and it didn't work i still get the same error message when i log in
any ideas?

(thanks in advance)

---


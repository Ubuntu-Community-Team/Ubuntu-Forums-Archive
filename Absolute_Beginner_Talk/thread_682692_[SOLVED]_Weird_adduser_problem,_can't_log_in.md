---
title: "[SOLVED] Weird adduser problem, can't log in"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by iris-n on 2008-01-30
Hi all

This morning i was trying to add a new user for my baby brother, and i ran through the weirdest problems.

I added trough the tty cli. Apart from lack of recognition of latin characters, that went fine.

When i tried to login, nothing. Weird. Logged back into my account, and tried to delete his account from the gui, but none were shown there. Gone to groups, and deleted his. But, all groups were deleted to! Even root.

So, now i couldn't login at all, even in recovery mode. Then i pasted the shadow and passwd files from my other pc, through the live cd, and now i can go in recovery mode, but the gui stays blocked, when i try to load it it halts in "Starting Hardware abstraction layer"

I managed to reach the gui from recovery mode using startx, but when i try t change users it gives me an gdm error.

I've never seen such an epoch fail before... anybody has any ideas on what to do?

Thanks in advance,

Iris

---

### Post by iris-n on 2008-01-30
up

This shouldn't be a hard issue, there isn't a way of resetting all users? Or to reinstall the desktop? Are the passwd and shadow the only files which deal with user configuration?

I definitely WON'T reinstall my gutsy.

I'm running a AMD Sempron, if that makes any difference.

---

### Post by sisco311 on 2008-01-30
> Are the passwd and shadow the only files which deal with user configuration?

/etc/group is  an  ASCII  file which defines the groups to which users belong.

---

### Post by iris-n on 2008-01-30
Oh, indeed, thanks.
But it didn't help =(

Anyway, this is the error message i get:

> 
(process:5355): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5359): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Could not get password database information for UID of current process: User "???" unknown or no memory to allocate password entry

Failed to start message bus: Memory allocation failure in message bus
EOF in dbus-launch reading address from bus daemon

---

### Post by iris-n on 2008-01-30
anyone? there isn't a way to reset all users or reinstall users-admin?

---

### Post by iris-n on 2008-01-30
please?

---

### Post by iris-n on 2008-01-31
up

---

### Post by iris-n on 2008-01-31
Solved it. In case anyone rans into a similar problem and fins the thread, this is the solution:

Copied, from a working system, the files /etc/passwd, /etc/shadow/, /etc/group and /etc/gshadow. Edited them so as to remove any users apart from the system ones (ANY trace of them). Be sure they've got the right permissons (640 for shadow and gshadow, and 644 for passwd and group). Boot in recovery mode, add a new user, and add him to the admin group. Login in his account. Recreate old users. But they still don't have their files, so:

```
cd /home
sudo chown -R <username>:<username> <username>
```

Hope it's of any use.

---


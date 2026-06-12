---
title: "Im in trouble I deleted all users except root!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by evandec on 2007-03-06
I was having trouble with my user account (hung everytime I logged in) so I logged in as root to delete the user and then add it again. 

I deleted the user at the command line and tried to add it again using the adduser command. However after I logged in as the user I created I got all sorts of errors with gnome. 

Also as root I can not use the ubuntu utility to add users. 

What am I to do now?

---

### Post by taurus on 2007-03-06
Boot into recovery mode from GRUB menu and run

```
useradd -m -G adm admin audio cdrom -s /bin/bash **john**
passwd **john**
```
Assuming **john** is your new login name.

Then, reboot and see if you can log in as **john** again.

```
shutdown -r now
```

---

### Post by evandec on 2007-03-06
I did that and all i got this...
```

Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
  -c, --comment COMMENT         set the GECOS field for the new user account
  -d, --home-dir HOME_DIR       home directory for the new user account
  -D, --defaults                print or save modified default useradd
                                configuration
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP for the new user account
  -G, --groups GROUPS           list of supplementary groups for the new
                                user account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           specify an alternative skel directory
  -K, --key KEY=VALUE           overrides /etc/login.defs defaults
  -m, --create-home             create home directory for the new user
                                account
  -o, --non-unique              allow create user with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new user
                                account
  -r, --system                  create a system account
  -s, --shell SHELL             the login shell for the new user account
  -u, --uid UID                 force use the UID for the new user account

```

---

### Post by taurus on 2007-03-06
Try

```

useradd -u 1000 -g 1000 -m -G adm admin -s /bin/bash john
passwd john

```

---

### Post by evandec on 2007-03-06
> **taurus said:**
> Try

```

useradd -u 1000 -g 1000 -m -G adm admin -s /bin/bash john
passwd john

```

Same problem as before.

---

### Post by taurus on 2007-03-06
What do your /etc/group & /etc/passwd look like?

```
cat /etc/group
cat /etc/passwd
```

---


---
title: "[SOLVED] root password"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2007-11-01
Ok, i feel like a complete tard, but I just installed ubuntu 7.10 server edition and I don't remember setting a root password, and I need root to make some configuration changes?  Is there a default password or a way to recover the password or do I just need to reinstall?

---

### Post by llamakc on 2007-11-01
> **richiewrt said:**
> Ok, i feel like a complete tard, but I just installed ubuntu 7.10 server edition and I don't remember setting a root password, and I need root to make some configuration changes?  Is there a default password or a way to recover the password or do I just need to reinstall?

There is not one. It's disabled by default. Logon as your user and type:

sudo -i

to get 'root' for a spell of time (fifteen minutes I think?).

To run one single command just prepend 'sudo' in front of it like such:

sudo emacs /etc/apache2/httpd.conf

or whatever.

---

### Post by BrendanM on 2007-11-01
By default Ubuntu sets the root password to a random password and suggests that you just use "sudo <command>" to temporarily gain root priviledges. If you really need to login as root for some reason, you can use the passwd command to set the root password.

---

### Post by richiewrt on 2007-11-01
Thanks, fixed my problem.

---

### Post by bodhi.zazen on 2007-11-01
> **BrendanM said:**
> By default Ubuntu sets the root password to a random password and suggests that you just use "sudo <command>" to temporarily gain root priviledges. If you really need to login as root for some reason, you can use the passwd command to set the root password.

close ...

By default the root account is locked and sudo is patched to allow this.

To enable the root account : ```
sudo passwd
```

To lock it again :

```
sudo passwd root -L
```

BUT : sudo -i and gksu (for graphical apps) is the way Ubuntu was intended.

---


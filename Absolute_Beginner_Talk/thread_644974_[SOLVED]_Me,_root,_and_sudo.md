---
title: "[SOLVED] Me, root, and sudo"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-12-19
Here's what I want, 2 different passwords.  1 is for my account. the other for root/sudo.

I've tried changing the root password, but it changes my password as well.

What am i doing wrong?

example... 
tom@localhost  password1
root@localhost password2
tom@localhost $ sudo -i (prompt for password2)

Thank you.
tom

---

### Post by Niniel on 2007-12-19
You misunderstood the idea of sudo.

There is root, and then there is you/sudo. 

Sudo gives you temporary root rights, and you use your own password for it. You need to be an administrator, but that's not exactly the same as the root account.

---

### Post by kernel tom on 2007-12-19
okay, so there is no way for me to have my login password different from the password i use for sudo?

---

### Post by PinkFloyd102489 on 2007-12-19
No, there isnt.

---

### Post by Bothered on 2007-12-19
To set/change the root password:

```
sudo passwd
```

Once the root password has been set sudo can be configured to require the root password for authorisation by:

```
visudo
```

By default, the file opened will contain a line:

```
Defaults        !lecture,tty_tickets,!fqdn
```

Add ",rootpw" to the end of this:

```
Defaults        !lecture,tty_tickets,!fqdn,rootpw
```

and save the file.

---

### Post by kernel tom on 2007-12-19
> **Bothered said:**
> To set/change the root password:

```
Defaults        !lecture,tty_tickets,!fqdn,rootpw
```



What does the !fqdn relate to?

---

### Post by svalding on 2007-12-19
I would imagine that this stands for Fully Qualified Domain Name

---

### Post by Bothered on 2007-12-19
I had to look that up in the man pages, but it relates to the use of fully qualified hostnames in the sudoers file (! => not, so this enables the use of short form hostnames). I haven't edited my sudoers file, so this option appears by default. For more info see:

```
man sudo
```

press "/", type "fqdn" and press return.

---

### Post by Bothered on 2007-12-19
> **Niniel said:**
> You misunderstood the idea of sudo.

There is root, and then there is you/sudo. 

Sudo gives you temporary root rights, and you use your own password for it. You need to be an administrator, but that's not exactly the same as the root account.

I largely agree with this, although there can be good reasons for wanting sudo to prompt you for a different password (e.g. if ssh ing from insecure machines).

---

### Post by kernel tom on 2007-12-19
> **Bothered said:**
> I largely agree with this, although there can be good reasons for wanting sudo to prompt you for a different password (e.g. if ssh ing from insecure machines).

and that is exactly my reason for wanting a different pwd for sudo

thanks for ur help

---


---
title: "Is this package installed?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by aparicio on 2008-01-13
Hello

I'm using Xubuntu (just installed).

If I try running ftpd, it seems like it's not installed:
```

$ ftpd
The program 'ftpd' can be found in the following packages:
 * krb5-ftpd
 * inetutils-ftpd
 * muddleftpd
Try: sudo apt-get install <selected package>
bash: ftpd: command not found

```

But if I try asking apt-cache whether it is installed, it looks like it is:
```

$ apt-cache search ftpd --installed | grep inet
inetutils-ftpd - File Transfer Protocol server

```

What's going on? Is it installed or not?

---

### Post by Rui Pais on 2008-01-13
Looks not installed. 
I think you need to:
```
sudo apt-get install ftpd
```

---

### Post by taurus on 2008-01-13
Are you trying to install a ftp server?

---

### Post by Dr Small on 2008-01-13
I generally use proftpd with gproftpd and it's always worked perfectly for me.

---

### Post by aparicio on 2008-01-13
Rui: Yes, I know the command to install it. I'm just trying to understand what's happening. Clearly apt-cache thinks it's installed, right?

taurus: Yes, I'm tryin to setup an ftp server. From what I've read, the procedure is to install inetd that then calls ftpd when needed. Is that right?

Dr. Small: What does that mean? What's the difference between those programs and ftpd, and why use those and not ftpd?

Thank you all.

---

### Post by taurus on 2008-01-13
If you want to have a ftp server, try installing either vsftpd or proftpd.  You could also use sshd too.

---


---
title: "Problem with new user account and vsftp."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Shack on 2007-07-14
Hi there.

I've been using vsftp for a while and it's been working fine.

Now I wan't to speed up my webpage updating so I made new user and this user is using /var/www as his homedirectory. 

I tried to login with this username to his homedir, but for some reason my ftp-server doesn't accept my password. I've changed this useraccounts psw for few times, but still I'm not able to login with this new account. 

I can login with my other accounts tought.

P.S. Is there guide how to control users and groups in terminal? I mean how can I list which users and groups I have and which are their homedirs etc.

Thanks.

---

### Post by asmoore82 on 2007-07-16
Check for a vsftpd log a in /var/log ...

My guess from experience with vsftpd from a _long_ time ago is that the ownership/permissions
of /var/www are too permissive for vsftpd's tastes ( hence the 'vs' in 'vsftpd' :)

P.S. /etc/passwd and /etc/group are the real locations of user/group information (plain text files :D)
format of entries in passwd is
username: password:user ID:group ID:Account  Name:home directory:login shell

format of entries in group is
groupname: password:group ID:members list, ...

the (unsecure) password field remains for historical reasons and is always 'x' on modern systems

---


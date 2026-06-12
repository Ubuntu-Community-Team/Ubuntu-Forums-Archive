---
title: "Web access on the FTP"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by tbresson on 2005-11-17
Hi.
I just installed vsftpd (Very Secure FTP Daemon) along with an Apache2 Web server.

vsftpd is setup with my user profile as ftproot so I have access to all that's in my profile but the web root is in /var/www/ which can't be reached via FTP at the moment.

How do I solve this? Do I need to make some kind of link with e.g. ln or what?

Thanks in advance for your help.

---

### Post by adwait on 2005-11-17
You could change the owner ship of the /var/www data to your userprofile using
```
chown <username> /var/www
```

After this though, apache2 may not be able to write to that directory....but in most cases it doesn't need to.

---

### Post by tbresson on 2005-11-18
I'm sorry, I don't see how taking ownership of the www folder makes it accessable from my profile dir.

wwwroot: /var/www
my profile: /home/username/

---

### Post by adwait on 2005-11-19
AFAIK, you can access all folders via FTP once logged in, but can't modify the ones you don't own. Basically, you can do everything that you can when sitting on the terminal. So if you change the ownership, you'll be able to edit the files. Atleast that's how it is on my end......anyone logging in can see all the files on the computer...

---

### Post by tbresson on 2005-11-19
Oh okay - that's not the case here.

I only have access to my profile folder, not the whole drive but thanks for trying :)

---

### Post by adwait on 2005-11-19
In /etc/vsftp.conf you might have set
> chroot_list_enable=YES

This setting restricts the users to their home directory (you are using your login on the machine to login via ftp as well, right??). If you set that to NO (or just comment it out by putting a # on the beginning of that line), that will alow you to mve around out of your home directory.
> chroot_list_enable=NO

---

### Post by tbresson on 2005-11-19
Hmm.. my settings are:
chroot_list_enable=NO
chroot_local_user=YES

I tried setting both to NO but no difference.

---

### Post by adwait on 2005-11-19
Uhh.....sorry I mean chroot_local_user

---


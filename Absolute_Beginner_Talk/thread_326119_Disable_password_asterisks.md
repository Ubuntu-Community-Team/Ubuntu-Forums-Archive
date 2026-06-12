---
title: "Disable password asterisks"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by J.Vega on 2006-12-27
Hi,

I've recently installed Ubuntu 6.10 edgy and now I want he gdm to not display the asterisks while entering a password (at the login screen, for examle). I succeeded to do so on SuSE Linux, but the same method doesn't work for Ubuntu, since there are some files which are not there or at another locaion in Ubuntu.
Does anybody know how to disable the asterisks? (and maybe the asterisks for every password entry, i.e. the screensaver or the password prompt when trying to start an administrative program as a normal user)
Thanks a lot in advance :)

Oh, and while we're at it...
How can I disable the trash bin, so that files are deleted immediately? :D

---

### Post by xyz on 2006-12-27
Hi,
The answer is I don't know but out of curiosity, may I ask why this is important to you?

To log in automatically:
System > Administration > Login Window 
Security Tab > Enable Automatic Login -Checked- and choose a user.

Everyone says it's not secure to "sudo" without prompt for password
```
gedit sudo visudo
```
find:
> system_username	ALL=(ALL) ALL
replace with:
> system_username	ALL=(ALL) NOPASSWD: ALL
save

---

### Post by J.Vega on 2006-12-27
Well one thing is that I just like it the way passwords are entered in the shell and the other thing is security... If you can't see how many letters a password has, it's harder to guess it ;)

so the autologin thing won't help me much, but thanks anyway

---

### Post by xyz on 2006-12-27
This may ring a bell...don't know really myself but I look in
/etc/pam.d

There's a bunch of files like "gdm,login,common-password"...

---

### Post by J.Vega on 2006-12-27
Those files seem to be no more than modules which include each other... but there are no real configuration files in there  ](*,)

---

### Post by J.Vega on 2006-12-27
I got it!
The prolem was as follows:
In /etc/gdm/gdm.conf-custom I set UseCirclesInEntry=false.
But in /etc/gdm/gdm.conf, there is another varibale, called UseInvisibleInEntry, which has to be set to true. After doing so and executing the command mentioned at the beginning of /etc/gdm/gdm.conf-custom, everything worked just fine :)

Thanks anyway ;)

---


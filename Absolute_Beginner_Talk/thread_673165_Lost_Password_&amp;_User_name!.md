---
title: "Lost Password &amp; User name!"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by JohnBUK on 2008-01-20
I installed Ubuntu from a live CD some months ago to "give a try" on an old PC and at the time entered a user name and password when requested. However I found I could not get onto the internet as my Wifi card was not supported (Linksys 54G). I therefore gave up. Now the new version has appeared I thought I would see if this was any different but since then have forgotten the UN and PW! 
I split my HDD so it would run the existing XP Pro and Ubuntu at the time and have a grub loader (whatever that is) but cannot log in to the old Ubuntu. I'm quite happy to delete the old partition (10Gb) and start again or is there a way of obtaining the UN and PW?
An idiots guide to either would be gratefully received.
Thank you.
JohnB

---

### Post by lluisanunez on 2008-01-20
Boot into recovery mode from GRUB menu and look at the output of this command.

```
ls -la /home
```

You should see a directory with your login name so all you have to do is change the password to something that you can remember this time. Assuming your login name is john, run

```
passwd john
```

---

### Post by Hallvor on 2008-01-20
Read this: 

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

edit: too slow

---

### Post by Peter1234123 on 2008-01-20
Well, first you boot from the LiveCD, then mount your hard drive (I believe it mounts by default) then open up a terminal and type "passwd root" and type a password the the user account "Root", then you'll have access to all the restricted files, type "su", and type that new password. There is a way to recover the password file (I think it's in /etc/users" or something like that) but, you can always go into xconfig, and allow graphic root login...that would do the trick.

---

### Post by JohnBUK on 2008-01-20
Good Lord, only posted a few minutes ago and I'm inundated with replies - thank you one and all!
I'll try and give these tips a go and will report back idc. Thanks once again.
JohnB

---

### Post by JohnBUK on 2008-01-20
OK, if I boot into Recover Mode then I eventually get an instruction which says something along the lines of "enter Root password or press Ctrl+D to continue. i don't know the Root password and Ctrl D takes me to the sign in screen!

Haliver's sugestion got me to a point where I have to put in a username which I have forgotten.

I haven't yet tried the Live CD but will do so tomorrow.

Lluisanunez suggestion also fails as I don't know my username - sorry!

Regards

JohnB

---

### Post by lluisanunez on 2008-01-21
> **JohnBUK said:**
> 

Lluisanunez suggestion also fails as I don't know my username - sorry!


You can find what your username is by looking into the /home folder, there will be only one folder there bearing your username, for example if I do
```
ls -la /home
```
I see the following:
```
drwxr-xr-x  3 root   root   4096 2007-12-05 15:49 .
drwxr-xr-x 21 root   root   4096 2007-12-23 00:34 ..
drwxr-xr-x 61 lluisa lluisa 4096 2008-01-21 18:06 lluisa

```
So I can deduce my username is lluisa

---


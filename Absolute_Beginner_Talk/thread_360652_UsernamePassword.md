---
title: "Username/Password"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by rhammond63 on 2007-02-13
I am completely new to Linux.  I installed ubuntu-6.10-alternate-i386.iso.  During the install I was asked for a password, but never a user name.  When I saw that, I even clicked on "back" to make sure I did not miss anything.  I completed the install.  System is now asking for username.  I tried root with the password I put in and without a password.  Suggestions other than re-install?  Thanks

---

### Post by taurus on 2007-02-13
Your username is **oem** and the password is the same that you created during the installing process.  Once you log in, don't forget to run this command so it would create an actual account for you to use everyday.

```
sudo oem-config-prepare
```

---

### Post by Rasidrew on 2007-02-18
I'm also a newbie to Ubuntu, and I have the same problem.  Installed the program, after wiping windows totally off my machine  with a password, but it never asked for a Username.  I tried oem as my user name and it did not work.  I also tried the ls / command and got the following:

bin
cdrom
etc
initrd
lib
media
opt
root
srv
tmp
var
boot
dev
home
initrd.img
lost+found
mnt
proc
sbin
sys
usr
vmlinuz

Help!  How do I determine what my username is so I can log in and start enjoying the world of Linux.

---

### Post by Maestro23 on 2007-02-18
> **Rasidrew said:**
> I'm also a newbie to Ubuntu, and I have the same problem.  Installed the program, after wiping windows totally off my machine  with a password, but it never asked for a Username.  I tried oem as my user name and it did not work.  I also tried the ls / command and got the following:

bin
cdrom
etc
initrd
lib
media
opt
root
srv
tmp
var
boot
dev
home
initrd.img
lost+found
mnt
proc
sbin
sys
usr
vmlinuz

Help!  How do I determine what my username is so I can log in and start enjoying the world of Linux.

What version did you download?  How did you install? (Nevermind, saw your other post).

---

### Post by bobosity on 2007-02-18
try this:

ls /home

What do see there?

---


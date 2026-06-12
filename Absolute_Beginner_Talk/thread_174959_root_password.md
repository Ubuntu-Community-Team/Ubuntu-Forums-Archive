---
title: "root password"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by garyvh on 2006-05-12
I have just started to learn linux, and this is my first go.  I am running from a live cd.  I don't know if I missed it or there is just a default that I don't know, but what is the root password for the live cd?  Or maybe there just isn't one?  Thanks in advance for any pointers.

Gary

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by aysiu on 2006-05-12
Ubuntu doesn't use root. It uses sudo.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

The default password on the live CD is no password.

So on a traditional Linux distro (say, Mepis), your terminal commands would look something like this on the live CD: ```
su
password:
apt-get update
apt-get install program
exit
exit
``` In Ubuntu's live CD, it would look like this: ```
sudo apt-get update
sudo apt-get install program
exit
``` In Ubuntu's installation, the password is your user password, assuming you have administrative privileges: ```
sudo apt-get update
password:
sudo apt-get install program
exit
```

---

### Post by NoUse on 2006-05-12
Root is disabled by default in Ubuntu.  Use sudo instead.

You can read more about it here.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by garyvh on 2006-05-12
Thank you for such a quick response.  I will try and figure this out.

Gary

---


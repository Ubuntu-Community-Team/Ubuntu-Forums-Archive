---
title: "upgrading from Release cantidate to full version?"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by iamdigitalman on 2006-06-02
ok, so I was using breezy a few days ago, then, I downloaded the RC ISO, and burned, and performed a clean install (just to have a little fun, plus I couldnt wait one more day). ran apt-get, and the update manager yesterday to get the full version, but nothing was availible. so, I thought I was fine, until I ran sysinfo, and this is the line I have:

> OS Type: Linux
Release: Testing/Unstable

is there any way to upgrade to the full version of Dapper? searched but found nothing.

thanks.

---

### Post by Jussi Kukkonen on 2006-06-02
RCs do update to the release version. I believe that sysinfo means Debian Unstable (which Ubuntu is based on).

you could do a
```
sudo apt-get update 
sudo apt-get dist-upgrade

```on the command line just to be sure

---

### Post by iamdigitalman on 2006-06-02
thanks, I did that, and it said 2 packages were availible. 

> app-install-data gnome-app-install

but I dont think those have to do with the whole distro?

oh well, i'll live with it. let's hope I keep reciving updates. if not, i can force them to show with apt.

-digital ;)

---

### Post by Jussi Kukkonen on 2006-06-03
iamdigitalman, I'm pretty sure your updates are working fine: those two packages appeared in the repos in the last 24 hours...

---


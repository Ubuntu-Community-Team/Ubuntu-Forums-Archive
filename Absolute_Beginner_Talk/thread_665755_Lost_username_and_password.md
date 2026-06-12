---
title: "Lost username and password"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by mtnboy40 on 2008-01-12
I know Write it down.  Got Ubuntu 7.10 all loaded rebooted and was logging in and I forgot the username and password I created hours ago.  How can I fix this?

---

### Post by eapache on 2008-01-12
As far as I know there is no way to recover it. If you honestly can't remember, just reinstall. And write it down, but keep it in a safe place.

---

### Post by kellemes on 2008-01-12
Boot into "rescue mode".

To reset the password of a user, type:
passwd [username]

---

### Post by taurus on 2008-01-12
Boot into recovery mode from GRUB menu and look at the output of this command.

```
ls -la /home
```
You should see a directory with your login name so all you have to do is change the password to something that you can remember this time.  _Assuming_ your login name is **john** (from the output above), run

```
passwd **john**
```
You have to type it in twice so be careful with that.  Then, reboot and see if you can log in as john with the new password.

```
shutdown -r now
```

---


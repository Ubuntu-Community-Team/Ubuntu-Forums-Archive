---
title: "Found Laptop"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Wallpanel on 2007-10-26
I found a laptop that someone was getting rid of, but it starts out with Ubuntu screens and asks for user name and password.  How do I get past the opening screens so I can use the computer?

---

### Post by taurus on 2007-10-26
If you don't know the login name and password, then you need to change it.  Boot into recovery mode from GRUB menu.  Then at the prompt, look to see what the username is by

```
ls -la /home
```
_Assuming_ it's john, change the password for john so you can now login as john with that new password.

```
passwd john
```
Reboot and see if you can log in as john with that new password.

```
shutdown -r now
```

---


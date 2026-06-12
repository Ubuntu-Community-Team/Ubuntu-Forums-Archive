---
title: "first time use"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by peterng25 on 2006-12-19
I have a weird little problem. I downloaded xubuntu following advice I saw on the Net, for an older laptop (128 MB RAM, 500mhz celeron).
It took a while to load, but installed completely. Then, on first boot, it came up directly to a login and password. Of course, I could not know them, since I wasn't asked during install. Can anybody offer any help?
Thanks in advance

---

### Post by macogw on 2006-12-19
Did you use the live or alternate cd?

---

### Post by sonny on 2006-12-19
During install you WERE ask to give a usernae and a password, to create a user for the sistem, that's what you should put... if you really don't remamber the process is simple... please post back if you want to create a new user.

---

### Post by taurus on 2006-12-19
Maybe you picked the oem version in which case it only asked you for a password.  So, your login name would be oem and your password is whatever the one you entered during the installing process.  After you log in, you need to run this command to create a regular account that you will use to log in from now on, removing oem account at the same time...

```
sudo oem-config-prepare
```

---

### Post by peterng25 on 2006-12-19
let me try oem. Thanks Taurus, it's a bit strange if one is not very familia with Linux. I did learn some Unix a while back, when linux was not graphical.
I think if I was asked for a password, I didn't get asked for a username, so that might be it.
I used the alternate cd, because I wiped windows 2k from the laptop and wanted to use linux permanently...

---

### Post by macogw on 2006-12-19
For future reference, the live cd does do permanent installation when you tell it to.

---


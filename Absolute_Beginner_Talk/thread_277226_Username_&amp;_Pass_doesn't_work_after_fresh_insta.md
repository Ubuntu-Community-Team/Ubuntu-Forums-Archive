---
title: "Username &amp; Pass doesn't work after fresh install"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Mafamaticks on 2006-10-14
Just installed Ubuntu on a seperate partition. The first part of the install went fine. I then had to run sudo oem-config-prepare to register a username and pass. I did that and it brung me to the login screen.

Now when I put it in it doesn't let me log in. Has this happened to anyone? Any solutions?

---

### Post by taurus on 2006-10-14
Make sure your cap lock is not on since Linux is case sensitive.  Otherwise, reboot your machine and at the GRUb menu, pick recovery mode and wait for it to finish booting.  At the prompt, change the password for that new user with

```
passwd john
(assuming john is your username...)

```

---

### Post by Mafamaticks on 2006-10-14
That's another thing. I tried some of the methods posted on here to recover a password. I tried the command passwd <username> and it doesn't recognize the username I put in. It won't recognize oem, sudo, or root as usernames either. I even tried to run sudo oem-config-prepare at the prompt to have the system ask me for a new username and pass, that didn't work either.

---

### Post by taurus on 2006-10-14
Boot into recovery mode and at the prompt, look at your /etc/passwd to see exactly what is the name of the user that you have created!  It should be the last line in /etc/passwd...

```
more /etc/passwd
```

---

### Post by steve.horsley on 2006-10-14
Even easier (probably) is **ls /home**.

---


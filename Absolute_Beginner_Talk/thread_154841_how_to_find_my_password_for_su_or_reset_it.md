---
title: "how to find my password for su or reset it"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-03
I just tired to install a program but when i typed the only password I know for my system, i get a Authentication failure message.

Can anyone help me reset the password?

---

### Post by johnnymac on 2006-04-03
Use the CD and boot into recovery mode - you should be able to reset the password then.....

when you boot with recovery mode you'll be in as root you should just have to type:

```
passwd
```

And it will have you change your password.

---

### Post by racermike1967 on 2006-04-03
I dont have access to a cd right now but if i did that same command in the terminal would it work?
I don't remember setting a password for root when i installed ubuntu.  I only remember one password I set up of my ubuntu and that's the one I use to login to my account.  All this time i thought i was logging into my root account.

---

### Post by stuporglue on 2006-04-04
Are you using su? By default su doesn't work, only sudo.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Try your command prefixed by sudo, then try your password when prompted.

---


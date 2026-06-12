---
title: "sudo not asking me for password"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-24
I did a couple of sudo commands earlier

and then a couple more,.... sudo isnt asking me for a password....

so i logged out, and back in

and i ran a sudo fdisk -l, it showed me without a password

i ran a normal fdisk, and got no output (which is correct)

whats going on?

---

### Post by moffa on 2007-05-24
After you use a sudo command, it doesn't ask you for 15 minutes.

You can kill the sudo process if you want it to start asking you immediately.

---

### Post by drowner on 2007-05-24
(i thought it had been 15 mins)

even if i log out?

---

### Post by Nikron on 2007-05-24
> **drowner said:**
> (i thought it had been 15 mins)

even if i log out?

If you terminate your session it should start asking you again.

---

### Post by drowner on 2007-05-24
it didn't!

This is very concerning to me.

---

### Post by drowner on 2007-05-24
h
i just ran gparted... and that asked me.

weird.

---


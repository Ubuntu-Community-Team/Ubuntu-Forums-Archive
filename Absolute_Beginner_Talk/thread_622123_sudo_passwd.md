---
title: "sudo passwd"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-11-24
I have included a screenshot to ask if this looks right. It appears I can change password at will, without entering the old password first. I even rebooted to see if I got the same result.

---

### Post by Rinzwind on 2007-11-24
That's cuz you typed your rootpassword within a certain period where the password is accepted as allready typed.

I get this: 

rinzwind@discworldLT:~$ sudo passwd
[sudo] password for rinzwind:

---

### Post by overdrank on 2007-11-24
> **spiderbatdad said:**
> I have included a screenshot to ask if this looks right. It appears I can change password at will, without entering the old password first. I even rebooted to see if I got the same result.

No that is not right I have to enter my password first! :confused:

---

### Post by ExBuM on 2007-11-24
You never typed in your password on that session and it still comes up with that?

---

### Post by nick_h on 2007-11-24
If you run passwd with sudo, then the passwd command will not request the old password.

However, sudo will ask for a password if you have not already entered one in the last 15 minutes.

---


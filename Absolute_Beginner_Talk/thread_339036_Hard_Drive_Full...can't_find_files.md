---
title: "Hard Drive Full...can't find files"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by handyguy33 on 2007-01-15
Our server runs ubuntu 6.0.6. When we came in this morning, we couldn't log in. As it turns out, the hard drive was reading 100% full. It's a 200GB drive and all of our files put together amount to about 80GB. The trash is empty and the folder properties agree with the amount that I know is there. Where is the other 100 or so GB of our hard drive space? Really need to solve this today, I have a flu and shouldn't even be at work right now.

---

### Post by taurus on 2007-01-15
Do you have any user on your server?

Boot into recovery mode from GRUB menu and look at your logs in /var/log.  Also, run this command at the prompt if you have users on your machine.

```
du /home
```

---

### Post by Paerez on 2007-01-15
if you ever can login (after freeing a little space) run "baobab" and point it to /. It will give you pretty pictures of your disk usage.

---

### Post by handyguy33 on 2007-01-16
That did it. We had an external backup drive that was unplugged, so the server was backing up on its own drive space. Thanks guys, I can go home and be sick now.

---


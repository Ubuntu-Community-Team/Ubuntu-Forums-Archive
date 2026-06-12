---
title: "I messed up my permissions"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by shingalated on 2006-11-01
I just made a rather large mistake,
```
chmod -R 777 /var
```]...once again my adhd / impulsiveness is showing](*,)  now sudo doesn't work...I'm sure I messed up enough other things doing this as well.  I'm afraid to see what else happens after a restart, but I guess the question I have is this: Is there any way to fix permissions?  A command or script or something would be helpful.  Thanks in advance!

---

### Post by taurus on 2006-11-01
So you can't use sudo at all now!  Try booting into recovery mode from GRUB and at the prompt, 

```
chmod -R 755 /var
```
Reboot and see what happens...

---

### Post by shingalated on 2006-11-01
well luckily I have  a password for the root user, so I was able to change the permissions for /var/run/sudo so sudo is now working okay, but I'm sure there are still other things that will not run.  Is there any way to restore the original permissions on /var?

---


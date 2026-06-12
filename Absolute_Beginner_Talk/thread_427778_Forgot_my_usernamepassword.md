---
title: "Forgot my username/password"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by shoopdawoop on 2007-04-29
How can I find it?

---

### Post by taurus on 2007-04-29
Boot into recovery mode from GRUB menu and look at the output of this command to see what your login name is.

```
ls -la /home
```
Assuming it's shoop, change shoop's password with

```
passwd shoop
```
Then, reboot and log in as shoop.

---

### Post by barbarella on 2007-05-10
Hey, I forgot my username + password, too.

I don't understand your response. Can you be more... specific?

---

### Post by taurus on 2007-05-10
Boot into recovery mode from GRUB menu and post the output of this command here then.

```
ls -la /home
```

---

### Post by Najand on 2007-05-10
If Taurus's reply is difficult for you, guys, use the following link at ubuntu wiki:
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by barbarella on 2007-05-10
Thanks, I got it, now. 
Taurus's reply is succinct & terse. When I used to play Zork, I'd always type in: 'maximum verbosity'. 

Again, thanks for your time and effort.

---


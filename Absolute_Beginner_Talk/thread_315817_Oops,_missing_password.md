---
title: "Oops, missing password"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by RickTaylor on 2006-12-09
Hello,

So I'm completely new to Linux and Ubuntu, and decided to try it on my home system. It loaded without a hitch (I have bootit, and used the special instructions to avoid loading grub over it), but when I tried to log in it didn't recognize my name/password combination. I thought I'd typed it in carefully, but I guess I made a mistake.

So what should I do now? Do I need to scrub the partition clean and start from scratch? Or can I just reload the system and expect it'll over-write itself in the appropriate ways? Or is there a simpler way to tweak a single file somewhere to fix it?

Thanks so much for your help.

--Rick Taylor

---

### Post by misha680 on 2006-12-09
Well if you select recovery mode when you are booting in GRUB, it will put you at a shell. To change the password of your user, type:
```
passwd username
```
where username is the user whose password you want to change. It will let you enter a new password for that user. Then just type exit to finish booting.

Misha

p.s. just noticed you did something else instead of grub. I am not familiar with bootit but if you can just add "single" to the kernel command line that is used to boot ubuntu in whatever utility you use, should get you the same effect (if you don't have recovery mode on bootit).

---


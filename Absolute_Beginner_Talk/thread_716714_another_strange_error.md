---
title: "another strange error"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by revanthedarth on 2008-03-06
I don't know how i was going to entitle it, so its "strange error" for now.

When i turn my PC on, i choose ubuntu to be booted. Then the Ubuntu loading screen comes, and then the command line. Last lines are, "fsck died with status8" i can't use any keywords, not even sudo and poweroff. I use this command: "cd /usr/bin" and then "poweroff", then the login screen comes, and everything is fine, including the console. Why does it happen? I use 2 OSs, can the other one be the problem? Or the hard disk?


Cool, now the pc restarts itself.

Should i format the drive that is failed to be fscked?

I did "fsck -y", but i did it when the gnome was on, not when i was on shell. But it doesn't fail anymore. Thanks.

---

### Post by taurus on 2008-03-06
Sounds like you may have to run fsck of your root partition by hand when it drops you into a shell.

```
fsck -y /dev/sda1
```
or whichever your / partition happens to be.

---


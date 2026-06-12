---
title: "superuser password?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-04-07
I'm learning a little command line operations but I can't use the su command because 
I don't know the password. I thought it would be my password i use to log in to the system but evidently not. I'm not on a networked computer. I just loaded edgy a few days ago & I'm the only user so nothing has been changed. did I miss something on my 
original installation or is there a way to find my password?

---

### Post by arochester on 2007-04-07
Use "sudo" not "su" and it will ask for a password = which is your password for logging on

---

### Post by Maestro23 on 2007-04-07
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by yabbadabbadont on 2007-04-07
You don't need to use su as Ubuntu is configured for the use of sudo instead.  If you need to drop into a root shell like su would give you, run ```
sudo -s -H
```

Edit: Wow.  Operation overkill.  :lol:

---

### Post by Maestro23 on 2007-04-07
> **yabbadabbadont said:**
> You don't need to use su as Ubuntu is configured for the use of sudo instead.  If you need to drop into a root shell like su would give you, run ```
sudo -s -H
```

Edit: Wow.  Operation overkill.  :lol:

That's right.  Rain down knowledge on the heads of the new people. :)

---

### Post by Kirk Fraser on 2007-04-07
I had the same problem this morning.  I found the answer on IRC Chat.  There is no password for the root in Ubuntu but you can use either of these commands according to a guy who claimed 10 years Linux experience:

sudo su
sudo -i

I haven't tried them but will soon -- I just noticed your request for the same thing and got registered to answer.  I hope it helps.

---

### Post by yabbadabbadont on 2007-04-07
> **Maestro23 said:**
> That's right.  Rain down knowledge on the heads of the new people. :)

Many, many years ago, when I was still in school, one of my teachers always said that the best way to learn something was through repetition, repetition, repetition.  He would be proud of us.  ;)

---

### Post by Maestro23 on 2007-04-07
> **yabbadabbadont said:**
> Many, many years ago, when I was still in school, one of my teachers always said that the best way to learn something was through repetition, repetition, repetition.  He would be proud of us.  ;)

I hear ya.  One of my college profs said the same thing to me about 15 years ago.:)

---

### Post by garyed on 2007-04-07
Thanks,
sudo works fine when I use my password.
I was working off an online tutorial so it I guess it was for an older distribution.
It also talked about using the command line to get to the terminal instead of using applications/accessories. I couldn't find anywhere on the interface to use a command line except inside the terminal.

---

### Post by yabbadabbadont on 2007-04-07
> **garyed said:**
> Thanks,
sudo works fine when I use my password.
I was working off an online tutorial so it I guess it was for an older distribution.
It also talked about using the command line to get to the terminal instead of using applications/accessories. I couldn't find anywhere on the interface to use a command line except inside the terminal.

Ctrl-Alt-F1 will drop you to the first system console.  (command line)  But (almost) anything you could do there can be done just as well in a terminal.  (Alt-F7 to return to your graphical environment)

---


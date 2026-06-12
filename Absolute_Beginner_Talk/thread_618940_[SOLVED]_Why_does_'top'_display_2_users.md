---
title: "[SOLVED] Why does 'top' display 2 users?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-20
Why does the 'top' command from terminal or via SSH display 2 users?
```
top - 23:43:02 up  2:33,  2 users,  load average: 0.00, 0.06, 0.20
```
I should be the only user logged on ???

---

### Post by Paul820 on 2007-11-20
There is root and the person that is logged in, you.

---

### Post by BassKozz on 2007-11-21
Ahh, that makes sense, thanks :)

---

### Post by jordanmthomas on 2007-11-21
> **Paul820 said:**
> There is root and the person that is logged in, you.

Actually, I belive both users are you.  You are logged in to the x server (gnome / whatever) and you are logged on in the terminal.

Anyway, you can type
```
who
``` to see who is logged on currently.

---

### Post by Paul820 on 2007-11-21
That's what i meant. But there is always a root user and usually that user is you anyway. They are both the same person. I should of explained it a bit better. :) S/he got what i meant anyway.

---

### Post by jordanmthomas on 2007-11-21
> there is always a root user and usually that user is you anyway
I believe you are mistaken here.  A typical user is **not** root.  In fact, I'd be willing to wager that since you're using Ubuntu, if you typed
```
last
``` root will have **never** logged in.

I swear I'm not trying to cause an argument or anything, but I am quite sure root is not logged in when you log in through gdm.  

On my computer, I am not root and who tells me that I am logged in twice, not me once and root the other.

Sure he/she got what you meant, but it wasn't right so they have a false nugget of information now.  Sorry to drag this out, but I don't think giving out incorrect information to users who are learning is a great idea.

---

### Post by BassKozz on 2007-11-21
You are correct, root has never logged in, just my "username" and "reboot" show up in last...
The results of who are ```
username    tty7         2007-11-20 21:10 (:0)
username    pts/0        2007-11-21 08:30 (:0.0)
```
Where "username" is my username, but why am I logged in twice, when I know I am not?
Could it be because I have SSH and VNC installed, and even thou they are not connected they are listening?

---

### Post by sisco311 on 2007-11-21
> but why am I logged in twice, when I know I am not?You are logged in your GUI(tty7) and in your terminal (pts/0).

>  Could it be because I have SSH and VNC installed, and even thou they are not connected they are listening?

pts/0 is the terminal in witch you typed the *who *command.You are logged in in this terminal.

---

### Post by mellowd on 2007-11-21
That's right, sometime I log in more than once via ssh. It'll show me logged in two or three times except just once

---

### Post by BassKozz on 2007-11-21
Thanks for all the help :D

---


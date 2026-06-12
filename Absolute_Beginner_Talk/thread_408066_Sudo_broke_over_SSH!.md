---
title: "Sudo broke over SSH!"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ceeg on 2007-04-12
Okay. SUDO broke. The only way to change your login as root with su - is by using the root password. To SET the root password in ubuntu, you have to use SUDO. I am using SSH so i cant boot into recovery mode.

---

### Post by Malakia on 2007-04-12
If I recall correctly when you boot into recovery mode your automatically root at login. I could be wrong about it to.

---

### Post by tonyr1988 on 2007-04-12
I'm confused. Are you trying to log in as root? If so, why? What's happening with your sudo so that it's broken? Does it not accept your password or what?

---

### Post by ceeg on 2007-04-12
> **tonyr1988 said:**
> I'm confused. Are you trying to log in as root? If so, why? What's happening with your sudo so that it's broken? Does it not accept your password or what?

it just doesnt DO anything. my /etc/groups file is messed up after running vigr somehow.

---

### Post by ceeg on 2007-04-12
> **Malakia said:**
> If I recall correctly when you boot into recovery mode your automatically root at login. I could be wrong about it to.

Can you boot into recovery mode through SSH? I doubt it :[

Gonna have to drive all the way across town then.

---

### Post by STREETURCHINE on 2007-04-12
what command were you trying to do, and what was the error message you got ?

---

### Post by ceeg on 2007-04-12
> **STREETURCHINE said:**
> what command were you trying to do, and what was the error message you got ?

ceeg@berith$: sudo vigr
ceeg@berith$:

Thats what it looked like.

---

### Post by jimarko on 2007-04-16
> **ceeg said:**
> ceeg@berith$: sudo vigr
ceeg@berith$:

Thats what it looked like.

I'm getting exactly the same problem, but locally, not on SSH.

The only thing that I've changed was my time settings, and after I got a timestamp error with the sudo command, I did sudo -k and switched to NTP..

I since cannot get sudo access at all....

---


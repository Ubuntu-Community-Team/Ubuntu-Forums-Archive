---
title: "Forgotten Root password"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by mwero001 on 2007-03-07
Hey people. I've forgotten my root password. Any ideas on how i can retrieve it?Help.

---

### Post by PriceChild on 2007-03-07
*moved and bumped*

When you boot you can choose the second kernel in the list to get to a root terminal.

From there you can "passwd username" to change that users password.

(I think) :)

---

### Post by Bachstelze on 2007-03-07
There is no root password in Ubuntu by default. If you *did* set one but forgot it, you can still use *sudo passwd* to reset it. If you just want to change your password, use the recovery mode as said above.

---

### Post by bry5an on 2007-05-24
hey, i forgot my root pw as well :( 

i tried booting to the 2nd kernel.. i assume that was the troubleshooting mode you were talking about. it came out with a long wall of text and eventually asked for my root pw (which i don't know) to continue with maintenance or press ctrl + D to continue. 

i tried using sudo passwd to reset it in root.. but i'm not sure i did that right. i did it in the terminal and it came up with a prompt asking me for my password.. plz help! 

oh, and it's entirely possible i'm doing something wrong.. i am a noob after all ;)

---

### Post by Bachstelze on 2007-05-24
When you do 

```
sudo passwd
```

it asks for *your* password and then lets you set a new root password.

---

### Post by bry5an on 2007-05-24
ohh.. ahh.. lol. ha. should've thought of that! much thanks! :D

---


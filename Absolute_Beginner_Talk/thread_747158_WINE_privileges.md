---
title: "WINE privileges"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-04-06
hihi!
Trying to run a wine application, and it prompts me saying that when run for the first time, the application must be run as administrator. I'm logged in with the only admin user there is though.. the one I usually use :D
Anyone know what can be done to amend this? tia!

---

### Post by TeoBigusGeekus on 2008-04-06
Have you tried?
```
sudo wine /path/to/executable/executable.exe
```

---

### Post by hungryOrb on 2008-04-06
aha! Thankyou, I'll try this now, any idea how to get past the windows spaces? Such as ones found in 'Program Files' and the directories/files within?

---

### Post by TeoBigusGeekus on 2008-04-06
Try to put quotes i.e.
sudo wine "home/yourusername/.wine/drive_c/Program Files/Path to exe/executable.exe"

---

### Post by hungryOrb on 2008-04-06
Thanks, I tried that actually, and it ran the thing, but still, I got the same message ;] Is there some kind of admin thing that must be toggled with the winemulator itself?

---

### Post by TeoBigusGeekus on 2008-04-06
Hm.... Could this be a message from the window$ program and not from Ubuntu? 
I mean, does the program require to be an administrator in window$ and not just a user?

---

### Post by hungryOrb on 2008-04-06
yes its a message from the program :/

---

### Post by TeoBigusGeekus on 2008-04-06
Unless someone else has something to propose, I would suggest using VmWare. 
The following link has some instructions that have worked for me.
[http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html]("http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html")
I'm trully sorry mate...

---

### Post by hungryOrb on 2008-04-06
Man you are really helpful ;D dont be sorry! :]
Thanks so much for all help ))))
I'll try the link ^.^:KS

---

### Post by Laser Dude on 2008-04-06
**You should *never* run Wine under sudo, or as root.**

If the program asks for administrator access, then that's a problem with the program, and it is not as solution to run it as root.  I've heard far too many stories in the few weeks I've been around about people who run all their favourite Windows programs under Wine as root, and wind up contracting viruses from them.

---


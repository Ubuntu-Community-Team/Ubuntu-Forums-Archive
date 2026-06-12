---
title: "How do you revert to earlier version of Kubuntu?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-09-26
I installed Dapper on my laptop, and everything seemed to work fine, but when I upgraded to Edgy, my wireless adapter stopped working for some reason.  I tried to install ndiswrapper to get it working again, but it didn't work.  Is there a way to go back to Dapper without reinstalling from scratch?

---

### Post by reckless2k2 on 2007-09-26
i don't think you can downgrade. sorry. post in another thread your wifi card info and we can get it up and running. if that's all that's holding you back, stay with 6.10. you can't get back to 6.06 without fresh install.

---

### Post by SuperCool4678 on 2007-09-26
> **reckless2k2 said:**
> i don't think you can downgrade. sorry. post in another thread your wifi card info and we can get it up and running. if that's all that's holding you back, stay with 6.10. you can't get back to 6.06 without fresh install.

I tried that before, and the stuff that people told me to do didn't work.

---

### Post by nwadams on 2007-09-26
upgrade to feisty

---

### Post by reckless2k2 on 2007-09-26
well if it didn't work in 6.10 then i'm sure the wifi wouldn't work in 7.04. it seems between the dropped drivers and the buggy network manager, he might be better with 6.06. haha.

---

### Post by mlind on 2007-09-26
you can do distribution downgrade using apt-pinning at least, there was a thread about this where one user successfully downgraded using this method. If you go for it, I suggest to remove each package that's not in   ubuntu-minimal or ubuntu-standard meta package (including ubuntu/kubuntu desktop), then change repositories, downgrade using apt-pinning and install kubuntu back.

---

### Post by reckless2k2 on 2007-09-26
HA! this guy can't get his wifi card to work on a 1-back release version. you think he's going to jump those hurtles? hahahahaha. 

pinning...minimal...remove...etc..etc..yadda..yadda..

i can tell you're ninja. haha..5 million beans and all..i'm jealous.

---

### Post by mlind on 2007-09-26
> **reckless2k2 said:**
> HA! this guy can't get his wifi card to work on a 1-back release version. you think he's going to jump those hurtles? hahahahaha. 

pinning...minimal...remove...etc..etc..yadda..yadda..

i can tell you're ninja. haha..5 million beans and all..i'm jealous.

lol, I was just trying to say it's possible :mrgreen:

---

### Post by reckless2k2 on 2007-09-26
yeah yeah yeah ninja. i know. keep drinking it up. hahahaha

---

### Post by nwadams on 2007-09-26
i have stuff that works on feisty that didn't on edgy

---

### Post by mac71 on 2007-09-26
> **nwadams said:**
> i have stuff that works on feisty that didn't on edgy

I'm with you. keep moving forward. i done an install of 6.06 on an old laptop. The touchpad didn't work. Nor did it in 6.10, but the machine was all singing and all dancing after upgrading to 7.04.

---


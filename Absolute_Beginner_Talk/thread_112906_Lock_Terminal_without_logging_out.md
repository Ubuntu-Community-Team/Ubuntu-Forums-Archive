---
title: "Lock Terminal without logging out"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by carlosqueso on 2006-01-05
Hey all, this is kind of a beginner question, so I'll ask it here.  I SSH to my home computer at work with PuTty, but often have to leave my desk for a short time.   Is there a way that I can have my home computer require a password to continue without logging out and closing the session?  Thanks in advance.

---

### Post by darckhart on 2006-01-05
could you lock the workstation on your end? (eg your work computer)

---

### Post by carlosqueso on 2006-01-05
I could...but was looking for a way to avoid that....nothing at my work is really that sensitive, I just want to protect my home computer from curious people messing with it.

---

### Post by darckhart on 2006-01-05
oh. well here's what i do.

it really depends on what you did on the home computer. like for my ubuntu box, i simply turn on the computer. that's it. so if you were to look at the monitor, all you would see is the login screen. 

when i ssh in from the other computer, it's like logging in for the first time. if you were to look at the ubuntu box's monitor after i had ssh'ed in, you would still only see the login screen.

---

### Post by carlosqueso on 2006-01-05
that's not my problem...my home computer's fine (I can lock the screen).  I want to lock my ssh session without disconnecting...it's really the only thing on my work comp that people might affect (they sometimes use my comp for the scheduling software on it when I'm away from my desk)

---

### Post by darckhart on 2006-01-05
ohh i see what you mean now. like lockdown putty or something. hmm good question. now i have the same question! hehe =)

---

### Post by carlosqueso on 2006-01-05
yeah...either lock down putty or the actual console itself.

---

### Post by benplaut on 2006-01-05
'away', 'lockvc', 'vlock' are all programs for the purpose (i think vlock is best). all are available through apt-get/synaptic :)

---

### Post by carlosqueso on 2006-01-05
Thanks! That's exactly what I was looking for! Now I can leave my ssh connection up when I step away without worry :-D  By the way....I agree with you...for what I want to do...vlock is really the only one that works.

---


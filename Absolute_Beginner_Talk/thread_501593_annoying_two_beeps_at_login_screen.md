---
title: "annoying two beeps at login screen :/"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by fsh on 2007-07-15
Hi, 

Since i installed nvidia drivers and beryl i get two beeps at login screen, apart from the normal drumming sound which i already switched off

those beeps are from pcspeaker, even with headphones attached you can hear them loud and clear in a room next to mine

i also have modprove -r pcspkr in my /etc/rc.local

plz help

---

### Post by r4ik on 2007-07-15
Video adapter is bad or is not seated properly.  Also, check to ensure the monitor cable is connected properly.

Good luck !

---

### Post by fsh on 2007-07-15
hmm, well, forgot to mention:

i'm running feisty 7.06 on dell d820 (quadra 120M) - so i can't really do what you suggested, 

but blacklisting the pcspkr did the job

the other thing is, that in nvidia settings instead of quadro 120m i get geforce go 7400 (someone said they re equivalent - is that true? )

---

### Post by r4ik on 2007-07-15
Sorry haven't got a clue.

---

### Post by testube_babies on 2007-07-15
> **fsh said:**
> 
the other thing is, that in nvidia settings instead of quadro 120m i get geforce go 7400 (someone said they re equivalent - is that true? )

Yes, they're the same chip with different firmware, so they are more or less equivalent.  My geforce go7300 shows up as its equivalent mobile quadro.

---


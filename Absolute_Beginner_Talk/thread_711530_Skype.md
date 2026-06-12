---
title: "Skype"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by grj23 on 2008-02-29
Hi

I (foolishly as I now see) installed Skype from [www.skype.com](www.skype.com) (who knew that would be so bad).  It actually worked, except for the microphone (i.e. I got as far as logging in, doing a test call, hearing the person talk, but not being able to hear my voice echoed back to me).

I went onto the Skype help and discovered that it needed OSS rather than ALSA.  This also turned out not to be true, but I faithfully went and did some stuff to do with emulating OSS, but this made no difference.

Further googling revealed that ALSA would have been fine but that installing from [www.skype.com](www.skype.com) wasn't so good, and I should use medibuntu.  So I started to do this and found that I couldn't because there was a previous version of Skype installed.

So I googled some more and discovered that I should do some whereis skype stuff and "remove" those.  This was a closed question which had a satisfied customer, so I gave it a try (it is probably painfully obvious that I'm very new to this ubuntu thing).  So I found the two files, and did a rm -r skype on them, and tried to install from the medibuntu, only to find that it was still installed.  I've also now read the warning about this.

I'm working on a newly installed 7.10.  

I'm trying to get this set up for a trip next week and am at the point where reinstalling the whole system seems like the question solution.  It feels like painful overkill, but I frankly don't understand a darn thing about anything, so if anyone can help I'd appreciate it.

---

### Post by melopsittacus on 2008-02-29
Hi, I suppose you installed Skype as a package, so why don't just try 
```
dpkg -r <skype package>
```?

---

### Post by grj23 on 2008-03-01
Hi

I tried this (I assume it's meant to be in the gnome-terminal at the root?!) and got the following error:

:/$ dpkg -r <skype package>
bash: syntax error near unexpected token `newline'


Thanks

---

### Post by genus_001 on 2008-03-01
I know this may not seem like the right answer, but i worked for me.  I installed skype from their website as well, and found that I also got no respone from the echo123 service.  After screwing around for a while, i opened up ALSA mixer and found my mic was muted.  After unmuting, it still wouldn't work, so i selected +20dB and finally i could talk with my friends.
Maybe this could work for you?
I hope so.

---

### Post by melopsittacus on 2008-03-02
> **grj23 said:**
> Hi

I tried this (I assume it's meant to be in the gnome-terminal at the root?!) and got the following error:

:/$ dpkg -r <skype package>
bash: syntax error near unexpected token `newline'


Thanks

Sorry, what I meant was

```
dpkg -r skype.deb
```

substituting skype.deb with the exact package name you had installed.

(I used the <...> notation meaning substitute here the name of the skype package; you should not enter <> into the shell :))

---


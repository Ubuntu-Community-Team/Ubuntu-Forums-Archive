---
title: "My password stop working O.O;"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Tanjer1588 on 2007-12-04
So for some reson my admin and screen name password stoped working and i dont know why, its really starting to freak me out, im running off the live cd right now but thats it. i need some kind of help any thing XD im freakin out over here

---

### Post by cmnorton on 2007-12-04
When you say stopped working, what does that mean? Can you not log in at all? Sounds like it.

As I recall you can give yourself a password-less account by editing /etc/shadow and blanking the second column from the left. Check these forms, however, for details on password-less accounts. You would edit this using the live CD.

Once you get back into your system, you'll need to reset your password. I'm curious as to how it stopped working.

---

### Post by K.Mandla on 2007-12-04
Restart the computer, log in to rescue mode and then change the password from the root prompt. Is that a solution for the problem?

---

### Post by Dr Small on 2007-12-04
> **K.Mandla said:**
> Restart the computer, log in to rescue mode and then change the password from the root prompt. Is that a solution for the problem?
And run:
```
passwd *username*
```

Fill in username with the user that you can not login with.

Dr Small

---

### Post by aysiu on 2007-12-04
More details (with screenshots) here:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Tanjer1588 on 2007-12-04
Thank you guys i will give theses a shot here in a min, Ill give you a run down of what happened see if it can help.

I cant log in at all, i was working in the terminal useing one of the howto: posts here on the forums i added something into my Fstab, since the howto was how to run a game via ISO it had to mount the ISO im guessing well i was testing it with diablo and i try to play the diable game and my system froze up so i had to restart, when i tryed to get back in my password didnt work, Before that happened the password was fine, it started acting up maybe 15 mins or so before i had to reboot, it was odd, i could not do a sudo command cus it said the password was wrong, yet i could get into anything under administration useing the same password, So could editing your Fstab effect your password?

---

### Post by Tanjer1588 on 2007-12-04
so i tryed the recovery thing and i seem to have the same problem it asks me for a password for root to the computer or to press Ctrl C to write through it, where then it takes me to the log in screen. So im in a bit of a situation here. Cus the root password for my computer was the same as my password

---

### Post by aysiu on 2007-12-04
You're not really supposed to have a root password. Now recovery mode is pretty much useless.

---

### Post by Dr Small on 2007-12-04
> **aysiu said:**
> You're not really supposed to have a root password. Now recovery mode is pretty much useless.
I was going to suggest John to try to crack it, but he has to have a copy of /etc/shadow with his password in it to crack it, and you have to use sudo to access that....

---

### Post by Tanjer1588 on 2007-12-04
would it be posible to install a 2nd boot of ubuntu on another partition then copy the files i need from the original partition onto the new one, then format the original?

---


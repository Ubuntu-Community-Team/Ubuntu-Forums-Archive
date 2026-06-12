---
title: "[SOLVED] Lost my installation user name and password"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by myCharlie on 2007-10-24
I just finish installed my first Linux OS using Ubuntu. I got the OS to start but when it ask for user name and password, I forgot what user name or password that I entered when installing the OS. How do I reset or recover my user name and password?

---

### Post by Dr Small on 2007-10-24
1.) Bootup in recovery mode, from GRUB
2.) You will be logged in as root. So type:
```
passwd *username*
```
(enter the username of the account password that you lost, where username is above)
3.) Reboot

Dr Small

---

### Post by magli on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=3609](http://ubuntuforums.org/showthread.php?t=3609)

---

### Post by magli on 2007-10-24
You said you also forgot your username. You could try typing 
```
cat /etc/passwd
```
Read the last few lines that result from this. One of them will be your username. You should recognize it.

---

### Post by myCharlie on 2007-10-24
Yes, I also lost my user name. Okay, so in the recue mode, I can type in:

cat /etc/passwd

and that will show my user name, correct?

---

### Post by Dr Small on 2007-10-24
> **myCharlie said:**
> Yes, I also lost my user name. Okay, so in the recue mode, I can type in:

cat /etc/passwd

and that will show my user name, correct?
Not right off the bat...
/etc/passwd shows the users and group settings of ALL the users on your system.
You'll have to look around, and as magli, look towards the bottom, and see if you recognize your account name.

Dr Small

---

### Post by myCharlie on 2007-10-24
> **magli said:**
> You said you also forgot your username. You could try typing 
```
cat /etc/passwd
```
Read the last few lines that result from this. One of them will be your username. You should recognize it.

Thanks! I got it working now. I can logged in fine after following your suggestion.

---

### Post by Dr Small on 2007-10-24
Please mark your thread as [SOLVED] from Thread Tools!
Thanks!

Dr Small

---


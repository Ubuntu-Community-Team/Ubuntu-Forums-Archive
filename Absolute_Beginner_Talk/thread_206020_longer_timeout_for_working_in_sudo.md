---
title: "longer timeout for working in sudo"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Optiker on 2006-06-29
Is it possible to change the length of time I can work using sudo operations without having to re-enter my password?

Thanks!
Optiker

---

### Post by harishg on 2006-06-29
One possibility is giving administrator rights to yourself by editing /etc/sudoers file.But that might be risky unless you know what you are doing.

---

### Post by Optiker on 2006-06-29
I think the reason it's risky is that if I do somthing stupid, I could kill the whole works! Sounds like there's no middle ground. In Windows, I have admin rights and rarely have gotten into trouble, but as a Linux novice, that might be too risky. Thanks...better put up with having to enter my PW.

Optiker

---

### Post by harishg on 2006-06-29
You can also give restricted administrator rights.I'm not sure how it can be done.Have a look at the man file for sudo and /etc/sudoers.

---

### Post by uzi09 on 2006-06-29
i'm not sure, but something that might help you out in the mean time is starting up a root account for a bit.

type:
```
sudo -sH
```
then when your done, just hit exit.

it's not all that dangerous. if you were to type a stupid command w/ sudo in front, you'll do just as much dmg as if you were to type it while in a root account. that's why they say not use it 24/7, no one said not to use it for a lil while :D

uzi

---

### Post by egon spengler on 2006-06-30
Type
```
sudo visudo
```

to edit your sudoers file. Add a line 

**Defaults timestamp_timeout = 15**

Now it'll be 15 mins before you're prompted for a password (default is 5 mins by the way)

---

### Post by Optiker on 2006-07-03
[QUOTE=uzi09]i'm not sure, but something that might help you out in the mean time is starting up a root account for a bit.

type:
```
sudo -sH
```
then when your done, just hit exit.

it's not all that dangerous. if you were to type a stupid command w/ sudo in front, you'll do just as much dmg as if you were to type it while in a root account. that's why they say not use it 24/7, no one said not to use it for a lil while :D

uzi[/QUOTE]

Good point...that would work ok in my low risk environment...single user at home.

Thnaks!
Optiker

---

### Post by Optiker on 2006-07-03
[QUOTE=egon spengler]Type
```
sudo visudo
```

to edit your sudoers file. Add a line 

**Defaults timestamp_timeout = 15**

Now it'll be 15 mins before you're prompted for a password (default is 5 mins by the way)[/QUOTE]

Ah-ha! I guess that's the sort of thing I was groping around for to start with...suspected it might be possible, just didn't know how. I did observe that in my old Breezy installation, it seemed longer than in my new Dapper installation - maybe just my imagination thought. Still, got me onto this track.

Thanks!
Optiker

---

### Post by Optiker on 2006-07-03
[QUOTE=egon spengler]Type
```
sudo visudo
```

to edit your sudoers file. Add a line 

**Defaults timestamp_timeout = 15**

Now it'll be 15 mins before you're prompted for a password (default is 5 mins by the way)[/QUOTE]

When I first do as you say above, I apparently get into visudo in the terminal, but it says I have to edit as root. If I open a new terminal session as troot, and then try to run visudo, I get the following message...
[I][COLOR="Teal"][B]
visudo: sudoers file busy, try again later[/B][/COLOR][/I]
What am I doing wrong?

Thanks!
Optiker

---

### Post by Optiker on 2006-07-03
Please disregard my previous reply. I managed to workaround.

Taking aysiu's recommendation in another thread to use kdesu instead of sudo, I launched Konqueror in root mode, then right-clicked on the sudoers file and selected "edit as root", which opened it for editing in kate. Added the line you suggested, and will now see how it works.

In any case, along the way, I learned how to properly run graphical apps as root, so that may take care of this issue as well.

Thanks!
Optiker

---

### Post by Sivik on 2007-02-15
I have done both a Defaults timestamp_timeout=0 and passwd_timeout=0 and i still get a syntax error.  I'm trying to make my sudoers to ask for a passwd everytime i use sudo in a command

---


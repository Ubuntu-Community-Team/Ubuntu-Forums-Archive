---
title: "&quot;Crashing&quot;"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2006-09-15
Could anyone tell me how you recover from a "crash" where everything stops responding (although music is still playing). I assume theres some magic key combo which will set things straight.

Thanks for the help.

---

### Post by xpod on 2006-09-15
if it does not compute....try reboot

---

### Post by DiJEH on 2006-09-15
lol. I assumed as much, but it seems most of the OS is still up if musics playing..

---

### Post by Dinerty on 2006-09-15
Is the terminal still functional?, if not you could restart X, which will take you to the desktop, saves the need for a hard reboot

ctrl + alt + backspace

---

### Post by Brunellus on 2006-09-15
> **DiJEH said:**
> Could anyone tell me how you recover from a "crash" where everything stops responding (although music is still playing). I assume theres some magic key combo which will set things straight.

Thanks for the help.
CTRL+ALT+Backspace will kill the Xserver (GUI), and bring you back to a login screen.

CTRL+ALT+F1 will bring you to a text login.  You can (usually) login here, then use command-line utilities like "top" to figure out what's using all your processor time.  Then, you can kill those processes one by one.

---

### Post by xpod on 2006-09-15
> ctrl + alt + backspace

IT did`nt rhyme:biggrin: ..sorry:frown:

---

### Post by jrcmuniz on 2006-09-15
> **xpod said:**
> IT did`nt rhyme:biggrin: ..sorry:frown:

CTRL+ALT+DEL ?! hehehe serious:

crtl + alt + f1 

ps -u your_user

kill -9 (number of process)

Cheers

---

### Post by Brunellus on 2006-09-15
> **jrcmuniz said:**
> CTRL+ALT+DEL ?! hehehe

Cheers
wrong OS.

---

### Post by anaconda on 2006-09-15
xkill
it kills any program which you click with your mouse. But to use it you should assign a key-combination for it.

or (more difficult) kill, if you get terminal working..
...

to get a terminal you can press Ctrl-Alt-F2

---

### Post by Brunellus on 2006-09-15
xkill is no good to a user if his Xsession is locked....

---

### Post by xpod on 2006-09-15
> CTRL+ALT+DEL ?! hehehe serious

Are you possibly having trouble seeing through your dirty windows?:-\"

---

### Post by jrcmuniz on 2006-09-15
> **xpod said:**
> Are you possibly having trouble seeing through your dirty windows?:-\"

No dude it was just a joke... try post number #7

sorry about that, ok?

Joao

---

### Post by xpod on 2006-09-15
EH?????????????????????????
You`ve lost me......i thought I was cracking the jokes?

I TOOOOOOOO was only joking mate......

wires crossed somewhere???:biggrin: 

Please dont apoligies to me EVEN if you have done something.Which you aint.
chill dude:rolleyes: ...(im scottish....i DONT get offended...at nothing!!)

---

### Post by ajgreeny on 2006-09-15
And if your keyboard is frozen I presume it is a reboot?

---

### Post by Brunellus on 2006-09-15
> **ajgreeny said:**
> And if your keyboard is frozen I presume it is a reboot?
yes, and a subsequent good grep through the logfiles, since anything *that* frozen is likely to be a bad driver issue.

---

### Post by mokmoki on 2006-10-27
how do you look at the said log files?

---

### Post by Brunellus on 2006-10-27
log files are kept in /var/log.  

I use cat to look through them:

cat /var/log/syslog

for instance.  that'll be really huge.  It is usually helpful to remember when (date & time) the problem happened, because then you can limit your investigation:

cat /var/log/syslog | grep Oct 19 | less

or things to that effect.  I'm away from a computer with a real shell.

older logs are kept in .gz file, for that, I think you'd need to zcat them or bzcat them.

---


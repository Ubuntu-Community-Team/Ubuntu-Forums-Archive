---
title: "Multiple Window Invasion"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-02-22
Hello Team

I was working in Gutsy just now when multiple windows starting opening up rapidly all over the place. As fast as I was closing them, more were opening. It reminded me of the multiplying broomsticks of the sorcerer's apprentice in *Fantasia*.

The concern was that when I clicked the top right button to restart, that window was rapidly overtaken by yet more windows opening. After much clicking I eventually managed to open a terminal and type "sudo reboot".

My question is:
Is there a strategy I should deploy if the same thing happens again? or indeed any other check I could or should make to ensure that things are working properly?

Kind regards

John

---

### Post by jan quark on 2008-02-22
hmm 

it is very unlikely but it sounds  like a malicious script from the good old windows days

you haven't installed anything from an untrusted source?

are there any hints in the system 

logs systes> administration >system logs

also take a look at the processes running
use these commands

```
top 
```

```
ps -A
```

---

### Post by justleen on 2008-02-22
perhaps some keys stuck?

I woould reboot though..
```
 sudo /etc/init.d/gdm stop 
```
this will kill Gnome Desktop Manager, shutting down just X.
(or just ctrl-alt-backspace to do the same)

---

### Post by agim on 2008-02-22
I had this happen once as well, with Tomboy. What programs were you running when this happened?
And to answer your question. I would just hit control-shift-backspace. That will restart x for you. There may be reasons not to do that, I am still relatively new to linux, but it got me out of that loop, when it happened.

Edit: control-alt-backspace, as in the above post

---

### Post by Andavane on 2008-02-22
> **jan quark said:**
> hmm 

it is very unlikely but it sounds  like a malicious script from the good old windows days

you haven't installed anything from an untrusted source?

are there any hints in the system 

logs systes> administration >system logs

also take a look at the processes running
use these commands

```
top 
```

```
ps -A
```

...yes, jan quark, I thought it was so Windozy that I had to look carefully to check what OS I was in.

I've looked at the logs, and typed in the commands you suggest but am afraid that what it says is way beyond me.

For the rest, as the other guys suggest, will use ctr-alt-bkspce should a similar panic arise again. I haven't installed anything today. The last thing I remember installing was gnucash. But I do remember looking at some ubuntu games last night, and some popup windows appeared, one of them offering me an ipod.

Regards,

John

---


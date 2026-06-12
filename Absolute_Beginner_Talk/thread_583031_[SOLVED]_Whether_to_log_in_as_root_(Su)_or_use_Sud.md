---
title: "[SOLVED] Whether to log in as root (Su) or use Sudo for xfce 4 task manager installat"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-10-20
I want to install "xfce 4 task manager" which was recommended to me by a friend for a certain problem I am trying to solve. He instructed me to do the following to install it:

> Install it in terminal, by logging in AS ROOT, do not use sudo, then at the prompt type

apt-get install xfce 4 task manager

And he told me how to make the administrative changes so I could log in as "Su". 

My question is: I am aware of all the dangers of "Su" posted in the Ubuntu Wiki and also by writers to this forum. Is it really the case that one has to log in as "Su" in order to install the above application? If so, why? And if not, then why would he have told me not to use Sudo for this particular install?

---

### Post by Dr Small on 2007-10-20
There is no harm in it.
Just do,
```
sudo apt-get install xfce 4 task manger
```
which i think should be xfce4-taskmanger or something

or:
```
sudo su
apt-get install *application-name*
```

Dr Small

---

### Post by swarup on 2007-10-20
I see. So is there no difference between using Su versus Sudo for this install? That is to say, there is no need to use Su in contrast to Sudo? Can you think of any reason he would have given me such an instruction not to use Sudo? Or perhaps, do you think he was mistaken in thinking that sudo cannot be used for this?

---

### Post by kerry_s on 2007-10-20
man just use synaptic. find it, click it, mark for install, click apply.

---

### Post by swarup on 2007-10-20
> **kerry_s said:**
> man just use synaptic. find it, click it, mark for install, click apply.

Yes, that is what I actually did ultimately. And it worked just fine. But I was just wondering for my own education, if indeed there is sometimes a reason that one HAS to use Su, and sudo will not do.

---

### Post by kerry_s on 2007-10-20
> **swarup said:**
> Yes, that is what I actually did ultimately. And it worked just fine. But I was just wondering for my own education, if indeed there is sometimes a reason that one HAS to use Su, and sudo will not do.

no, sudo can do it all, the equivalent of su is> sudo su
this allows you to be root with out having to activate root with a password.
i use debian which has su standard, but i always switch everything to sudo.

here is just a part of my menu, you can see i use sudo to call xterm to put my password then execute the program. i don't even have gksu installed.
see pic->

---

### Post by swarup on 2007-10-20
I see. That is great to know. Thank you.

---


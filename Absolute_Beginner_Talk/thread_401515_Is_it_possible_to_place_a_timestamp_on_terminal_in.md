---
title: "Is it possible to place a timestamp on terminal input lines?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by seeknowsage on 2007-04-04
I have recently installed ubuntu and would like to know if it is possible to place a timestamp on the input lines in the terminal. Thanks for your time.

---

### Post by Jussi Kukkonen on 2007-04-04
> **seeknowsage said:**
> I have recently installed ubuntu and would like to know if it is possible to place a timestamp on the input lines in the terminal. Thanks for your time.

I assume you mean the prompt?

the prompt is built from the contents of variable PS1 (usually), this is what it looks by default:
```
${debian_chroot:+($debian_chroot)}\u@\h:\w\$
```
The important part is the end (\u = user, \h = hostname,  \w = working dir).You can add the time there in several ways, with this being the easiest:
```
PS1="${debian_chroot:+($debian_chroot)}\t \u@\h:\w\$ "
```
Notice the "\t". You can just run that in a terminal, but you'll have to do add that to a startup script (.bashrc usually) if you want it automatic.

More info: [http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html)

---


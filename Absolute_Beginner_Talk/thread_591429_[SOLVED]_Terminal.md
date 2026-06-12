---
title: "[SOLVED] Terminal"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by snerd on 2007-10-25
I was in the process of installing the java 6 but got interrupted somehow. Now I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I try that I get this:

dpkg: requested operation requires superuser privilege

So I'm a complete noob, how to proceed?

I got messed up when the java tos stuff came up, and at the bottom it said <ok>. I couldn't figure out how to OK the damn thing! Hitting Enter did nothing so I just closed the terminal window, which screwed it up.

---

### Post by kellemes on 2007-10-25
> **snerd said:**
> I was in the process of installing the java 6 but got interrupted somehow. Now I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I try that I get this:

dpkg: requested operation requires superuser privilege

So I'm a complete noob, how to proceed?

I got messed up when the java tos stuff came up, and at the bottom it said <ok>. I couldn't figure out how to OK the damn thing! Hitting Enter did nothing so I just closed the terminal window, which screwed it up.

Type..
```
**sudo** dpkg --configure -a
```

The added **sudo** is to get superuser-privileges.. you will need this in the future also..

---

### Post by indytim on 2007-10-25
at the terminal try:

sudo dpkg --configure -a

IndyTim

---

### Post by paul.matthijsse on 2007-10-25
hello,

put 'sudo' in front of that dpkg command, it'll ask for your password and after that it works -- usually:.. :-)

---

### Post by snerd on 2007-10-25
Thanks everyone, that did it. I hate the noob stage!  :mrgreen:

Now, when I get a eula screen in terminal when installing the java 6 stuff, how do I do the "ok" agreeing to it? I tried hitting enter but nothing happened.

edit: I deleted my XP installation last night and installed this as my only operating system. So now I HAVE to learn it!

---

### Post by kellemes on 2007-10-25
Seems obvious [ENTER] should do it.. strange..
Have you tried [SPACE] or [TAB]?

---


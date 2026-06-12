---
title: "Can't open TTY sessions"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by jakedahn on 2007-06-13
Hey, can someone help me? I've been having problems with switching to a TTY session by hitting ctrl+alt+f1 (and also f2-6). I'm using 7.04.

---

### Post by Happy_Man on 2007-06-13
And what exactly does it do?

---

### Post by jakedahn on 2007-06-13
Nothing at all, there is no response. It just stays in gnome.

---

### Post by Happy_Man on 2007-06-13
Quite odd..... as far as I know, that's one the most basic commands. It really should work......

---

### Post by jakedahn on 2007-06-13
Well... it doesn't.

---

### Post by Khaled Khalil on 2007-06-13
me too, i have this problem since today morning !
i swear it was working just fine until yesterday, last time i was playing with extra X servers and had no problem at all !

any one know at what level such shortcut is configured ?
of course it is not by window manager, also not by X server configuration (ctrl+alt+back_space works normally)

there is also [another post]("http://ubuntuforums.org/showthread.php?t=472647") today about the same issue, i will link each other in case if someone suggested a solution

---

### Post by jakedahn on 2007-06-13
Hmm strange that everyone is just getting this today. It was also working for me just fine yesterday.

---

### Post by pmg on 2007-06-14
Do you have **getty** processes running on the ttys?  Run "**ps auxw | grep getty**".  You should have a **/sbin/getty** running on each of tty1 - tty6.

---

### Post by jakedahn on 2007-06-14
getty is running on all of them, here's the output:

> jakedahn@linux:~/ $ ps auxw | grep getty
root      4325  0.0  0.0   1652   512 tty4     Ss+  Jun13   0:00 /sbin/getty 38400 tty4
root      4326  0.0  0.0   1652   512 tty5     Ss+  Jun13   0:00 /sbin/getty 38400 tty5
root      4330  0.0  0.0   1648   512 tty2     Ss+  Jun13   0:00 /sbin/getty 38400 tty2
root      4331  0.0  0.0   1652   508 tty3     Ss+  Jun13   0:00 /sbin/getty 38400 tty3
root      4332  0.0  0.0   1652   512 tty1     Ss+  Jun13   0:00 /sbin/getty 38400 tty1
root      4333  0.0  0.0   1648   508 tty6     Ss+  Jun13   0:00 /sbin/getty 38400 tty6
jakedahn 25079  0.0  0.0   2884   772 pts/0    R+   01:50   0:00 grep getty

---

### Post by Khaled Khalil on 2007-06-15
jakedahn, i found a solution
try to reinstall "xkb-data"
it worked for me, i hope it will solve your problem [-o<

pmg, actually it is not about ttys themselves, but the keyboard binding that steel keyboard attention, xkb-data do this in X, so just after i start X the problem appears, but without it, for example when i logged to the recovery start-up i was able to switch normally, until i started X,
but thanks for your help, i learnt from you about getty :)

for how i got this, i just posted in the [other thread]("http://ubuntuforums.org/showpost.php?p=2848336&postcount=10")

---

### Post by DonnieP on 2007-06-16
OK, I've got the exact same problem.  No ttys at all.  I don't know how long I've had the problem because I rarely use the console, but I noticed it real quick when I installed fluxbox (from Synaptic and the package's menus are broken) and the only thing I could do was ctrl-alt-backspace.  I'm on Feisty by the way.  I logged back into GNOME and sure enough no ttys there either.  I have twice done the xkb-data reinstall suggested in this thread and it has not solved the problem for me.  What gives?

---

### Post by DonnieP on 2007-06-17
Well, I finally happened on a fix, but I have no clue what actually caused the problem in the first place.  As stated above, no joy on xkb-data re-install.  However, reinstalling the console-setup and console-tools packages took care of it for me.  Very strange.

---


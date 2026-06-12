---
title: "apt-get vs aptitude?????"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-25
Okay, here is my quesiton:  I was trying to install NFS on my ubuntu box.  I decided to use command apt-get install NFS and it didn't work.  I then decided to use aptitude NFS and to my surprise it worked.  What is the difference?](*,)

---

### Post by nanotube on 2006-05-25
well, aptitude better keeps track of dependencies and stuff... but it shouldnt matter for the purposes of being able to install stuff. so i am not sure what happened there. maybe aptitude auto-updated the package list before installing.?

---

### Post by NeoGreen on 2006-05-25
Yeah it probably did.  Thanks for the information.:)

---

### Post by Sef on 2006-05-25
aptitude works better when you decide to uninstall something.  It will uninstall it all.

---

### Post by confused57 on 2006-05-25
I just wanted to bump this thread up to mention a problem I had.  I have Dapper installed along with Xubuntu-desktop, for 3 or 4 days during the searching for updates on my computer, I kept getting "Xubuntu-desktop skipped". I tried doing apt-get update and apt-get dist-upgrade both from the terminal and in the text command prompt(after shutting down GDM), with no success.

I posted the problem in the Dapper Section of the forum and someone suggested using "aptitude", instead of apt-get...worked like a charm...resolved any dependencies, uninstalled unnecessary packages and installed ones I needed.
I'm no longer getting the "Xubuntu-desktop skipped" message.

---

### Post by uzi09 on 2006-05-25
with apt-get lagging so far behind, y bother with it? everywhere i look, i see apt-get like 99% of the time. y not just stick with aptitude?

---

### Post by aysiu on 2006-05-25
[QUOTE=uzi09]with apt-get lagging so far behind, y bother with it? everywhere i look, i see apt-get like 99% of the time. y not just stick with aptitude?[/QUOTE] Habit, I think, mostly.

Ignorance.

Fear of the unknown.

---

### Post by uzi09 on 2006-05-25
well, if i'm not missing out on anything while using aptitude, i might as well stick with it...

---

### Post by NeoGreen on 2006-05-25
I've started to use aptitude more because while configuring my linux box (which I am Ubuntu 5.10) most installs work with aptitude than with apt-get.  I don't know why,but they do.:-k

---

### Post by uzi09 on 2006-05-25
that *is* interesting.
there are a whole lot more options under aptitude too -- and they seem a lot better!

geez - i can't believe i've been missin out on this :S it's like not trying out linux ](*,)

EDIT: one thing i've noticed in a few programs is this line at the end of the help file:
"This aptitude does not have Super Cow Powers."

anyone care to explain what that's supposed to mean???

---

### Post by NeoGreen on 2006-05-25
Hey, Ive seen that tooo!!!!!! :o  What does that mean???](*,)

---

### Post by aysiu on 2006-05-26
[QUOTE=uzi09]
EDIT: one thing i've noticed in a few programs is this line at the end of the help file:
"This aptitude does not have Super Cow Powers."

anyone care to explain what that's supposed to mean???[/QUOTE] Apparently, we'll never know why:
[http://lists.debian.org/debian-user/2003/01/msg01671.html](http://lists.debian.org/debian-user/2003/01/msg01671.html)

---

### Post by uzi09 on 2006-05-26
hmm, interesting....sounds like Da Vinci code stuff lol, gotta hide some big hugh secret :\

---

### Post by confused57 on 2006-05-26
[QUOTE=aysiu]Apparently, we'll never know why:
[http://lists.debian.org/debian-user/2003/01/msg01671.html](http://lists.debian.org/debian-user/2003/01/msg01671.html)[/QUOTE]

One of the replies in the thread had this:

[http://lists.debian.org/debian-user/2003/01/msg01699.html](http://lists.debian.org/debian-user/2003/01/msg01699.html)

---

### Post by uzi09 on 2006-05-26
btw: going back to the topic, here's a good thread about this...

[http://www.ubuntuforums.org/showthread.php?t=164082](http://www.ubuntuforums.org/showthread.php?t=164082)

---

### Post by nanotube on 2006-06-08
[QUOTE=confused57]One of the replies in the thread had this:

[http://lists.debian.org/debian-user/2003/01/msg01699.html](http://lists.debian.org/debian-user/2003/01/msg01699.html)[/QUOTE]
try the following two commands:
```
apt-get moo
aptitude moo
```
and it will shed some more light on the situation :)

---

### Post by uzi09 on 2006-06-08
lol, yah, i saw that in someones sig. c00l stuff :D

i guess that's one thing apt-get has over aptitude :lol:

but i'm still curious y there are 2 seperate ones - wouldn't life be easier for everyone (especially the devs) if they just stuck with one?

---

### Post by nanotube on 2006-06-08
[QUOTE=uzi09]lol, yah, i saw that in someones sig. c00l stuff :D

i guess that's one thing apt-get has over aptitude :lol:

but i'm still curious y there are 2 seperate ones - wouldn't life be easier for everyone (especially the devs) if they just stuck with one?[/QUOTE]
well, it appears to be just about the only thing apt-get has over aptitude, i must say :)

there are two separate ones because aptitude was developed after apt-get. so aptitude is there because it's better, and apt-get is there for backward compatibility and because people are used to it, i'd say.

check out the faq entry on aptitude vs apt-get in the third link in my sig.

---


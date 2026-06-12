---
title: "I need a little help removing things from ubuntu."
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-10-23
I need help removing Some things.

One: the EasyUbuntu icon under: Applications >> System tools.

Two: since EasyUbuntu never worked for me, can i delete the files it downloads?

Three: When i go to add remove programs i can remove "amaroK" the music player. it says one or more programs need it to function proply. but i dont see how this could be true because i only downloaded and used it once.

could any one help me remove these three things?

---

### Post by Sef on 2006-10-23
> Three: When i go to add remove programs i can remove "amaroK" the music player. it says one or more programs need it to function proply. but i dont see how this could be true because i only downloaded and used it once.

Likely there are dependency issues.  AmoroK and something else share the same dependencies, so removing the former would create problems for the latter.

---

### Post by Jamesbowden on 2006-10-23
so how can i solve this problem?

---

### Post by Jamesbowden on 2006-10-23
/bump

---

### Post by jorn on 2006-10-23
There is something about removing Easy Ubuntu here:
[http://ubuntuforums.org/showthread.php?t=257767](http://ubuntuforums.org/showthread.php?t=257767)
Hav'n tried it myself.
If the uninstallation of Amarok warns you about dependencies, just keep it.
It doesn't do any harm.

---

### Post by xyz on 2006-10-23
> **Jamesbowden said:**
> so how can i solve this problem?
I guess you don't solve this pbm!
As stated above, Amarok and Progs x,y or z use the same dependencies to work...so either you keep Amarok or you try to find out which progs share those dependencies and decide if you need them!
If I were you, I wouldn't waste my time on that.

How did you install EasyUbuntu?

---

### Post by Jamesbowden on 2006-10-23
i managed to remove them my self by doing:

sudo apt-get remove easyubuntu.

and

sudo apt-get remove amarok

didnt realy take much thinking, i always expect that i will have to do things the hard way, and jump strait to dinign things the hardway instead of trying the easy way first.

another curse on being an exwindows user i supose.

---

### Post by xyz on 2006-10-23
> **Jamesbowden said:**
> i managed to remove them my self by doing:

sudo apt-get remove easyubuntu.

and

sudo apt-get remove amarok

didnt realy take much thinking, i always expect that i will have to do things the hard way, and jump strait to dinign things the hardway instead of trying the easy way first.

another curse on being an exwindows user i supose.

Good for you! I just hope that removing Amarok will not make ptoblems for you using other progs you may need. That was Sef main point!

---

### Post by Titus A Duxass on 2006-10-23
A tip for next time - Try and avoid apt-get for this sort of thing.  Use aptitude, it is a smarter packet and will not leave you with so many issues.

---

### Post by Jamesbowden on 2006-10-23
thanks for your help

---

### Post by xpod on 2006-10-23
Is`nt "apt-get" mabey better in this case if he did`nt want to remove the dependancies?.....
I use "aptitude" too but if i did`nt want to be rid of all the dependancies then mabey "apt-get" is the better choice in that case:confused: 

And does that mean that a program "needs" those dependancies or can it not also just mean that the program can "use" them in some way but might not actually "need" them.?

I`m 3 months down the road and using edgy now but i still cant get my head round most of it.....
Great fun trying though

---

### Post by Titus A Duxass on 2006-10-23
Maybe you are correct. But with aptitude you can see what is being removed easier and therefore can reinstall (with aptitude) the relevant parts.

There are one or two of us advocating the use of aptitude over its cousin apt-get.

But at the end of the day, it's horses for courses as ever with linux.

---

### Post by Ben Sprinkle on 2006-10-23
> **xpod said:**
> Is`nt "apt-get" mabey better in this case if he did`nt want to remove the dependancies?.....
I use "aptitude" too but if i did`nt want to be rid of all the dependancies then mabey "apt-get" is the better choice in that case:confused: 

And does that mean that a program "needs" those dependancies or can it not also just mean that the program can "use" them in some way but might not actually "need" them.?

I`m 3 months down the road and using edgy now but i still cant get my head round most of it.....
Great fun trying though

Daen't a wee bit are we?
Tis a melt-down withoot the dependencies mate. \\:D/

---


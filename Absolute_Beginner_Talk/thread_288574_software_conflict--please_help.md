---
title: "software conflict--please help"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by benner on 2006-10-30
I am trying to install a program called 'childsplay' on 3 edgy edubuntu machines in my classroom.  i tried the 'add remove programs' and got the following error message:

This application conflicts with other installed software.  To install 'childsplay' the conflicting software must be removed before.  Switch to the advanced mode to resolve this conflict.

So i ran synaptic and tried to install 'childsplay'.  it wouldn't install it because i don't have python-pygame installed.  so i tried to install 'python-pygame' and it wouldn't install it because i don't have 'pyton 2.4-pygame' installed.  i couldn't install that unless 'python 2.4-numeric-ext' installed.  then synaptic couldn't locate 'python 2.4-numeric-ext.  

the funny thing is that i have the exact same machine running the exact same OS with exactly the same updates at my home and had no trouble installing it.  the ONLY difference between the machines is that the ones at school have 'afterbirth' (a tweaked version of automatix) installed while the one at home has automatix2.   

this program has reading programs on it for my grade 2 students to use.  successful implementation of the program takes me one step closer to convincing the school to ditch windows entirely for linux.  if you love linux and you want to see a new generation of pc users heading in that direction, help a teacher /linux newbie get his machines sorted (in the past, i seem to get a pretty low response rate to queries).

---

### Post by Jussi Kukkonen on 2006-10-30
> the ONLY difference between the machines is that the ones at school have 'afterbirth' (a tweaked version of automatix) installed while the one at home has automatix2.
I would not be at all surprised if this was the reason.

You could try installing childsplay with apt-get or aptitude from the command line, there are often better error messages there:
```
sudo aptitude install childsplay
```

---

### Post by land0 on 2006-10-30
I would suggest copying the exact repository /etc/apt/sources.list from your home machine over to the school machines. Remove the version of python that rebirth installed if any and use Automatix2 to install Python if that is what you did at home. That is if you used either app to install python in the first place. The idea being to emulate as close as possible the same environment that the application has all of the dependencies solved. Try testing this approach on one of the machines and go from there. 

I hope this helps

---


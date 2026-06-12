---
title: "groupwise 7 will not completly load."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by weezerisrock on 2007-09-20
I'm not sure what the deal is.  I installed it just the other day, converted the RPM with alien and everything installed great.  When I start the program it runs and prompts me for my password.  (this is after the first time it prompted me for the server and username and such.)  After I enter in my password, a new window appears titled groupwise.  However this is as far as it goes.  The window stays white and never loads anything else.

Anyone have anything I could try?

---

### Post by Daveth on 2007-09-20
what does it say if you launch it from a terminal then?

---

### Post by weezerisrock on 2007-09-20
forgive my noobness,

How do I launch it from terminal?  If I do an alt+f2 then I have the option to run it in terminal but then auto archiver tries to open....  weird.

If I open the terminal and browse to the path (which I know) then how do I start it?

---

### Post by Daveth on 2007-09-20
sorry, should just be 

```
Groupwise
``` or possibly

```
groupwise
```

it is case senstive. And I'm assuming Novell call it that!

If you goto Applications/ Accessories, you can by right clicking on it, add the terminal launcher to a panel. Always handy just to have it sitting there.

---

### Post by weezerisrock on 2007-09-20
```
mckayr@frodo:/opt/novell/groupwise/client/bin$ groupwise
bash: groupwise: command not found

```

weird eh?  There is no caps on it.  this is the dir.

```
mckayr@frodo:/opt/novell/groupwise/client/bin$ dir
groupwise  groupwise-bin  groupwise.sh  XisErr.xml

```

---

### Post by dcstar on 2007-09-20
> **weezerisrock said:**
> ```
mckayr@frodo:/opt/novell/groupwise/client/bin$ groupwise
bash: groupwise: command not found

```

weird eh?  There is no caps on it.  this is the dir.

```
mckayr@frodo:/opt/novell/groupwise/client/bin$ dir
groupwise  groupwise-bin  groupwise.sh  XisErr.xml

```

```
./groupwise
```

---

### Post by aklein24 on 2007-10-04
I have this problem as well, and can't figure out what's going on...

-Andy

---

### Post by weezerisrock on 2007-10-05
I'm making a second attempt at it.  This time loading Java before loading groupwise.  I'll let you know.

---

### Post by TalioGladius on 2007-10-05
I'm having a similar problem but I'm farther along than you.


you need to execute the goupwise.sh file, not the plain old groupwise

---

### Post by aklein24 on 2007-10-05
Hey, I figured out my problem. If you have any sort of 3d desktop enabled, (aka compiz, emerald) java goes wonky and won't show the contents of an application window. So, since groupwise is a java app, you won't see anything. Disable compiz/emerald/beryl, and it should solve your problem.

-Andy

---

### Post by TalioGladius on 2007-10-05
> **aklein24 said:**
> Hey, I figured out my problem. If you have any sort of 3d desktop enabled, (aka compiz, emerald) java goes wonky and won't show the contents of an application window. So, since groupwise is a java app, you won't see anything. Disable compiz/emerald/beryl, and it should solve your problem.

-Andystill get the same thing


eckertc@ITS-128224:/opt/novell/groupwise/client/bin$ /opt/novell/groupwise/client/bin/groupwise-bin: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory

---

### Post by weezerisrock on 2007-10-08
3d desktop ended up being my problem too.  grrrrr.

Talio, have you tried removing and reinstalling java?

---

### Post by aklein24 on 2007-10-16
Anyone looking for solutions in this thread see this:

[http://ubuntuforums.org/showthread.php?t=147278&highlight=groupwise](http://ubuntuforums.org/showthread.php?t=147278&highlight=groupwise)

I've posted info about most of the problems talked about here, including the java error and 3d desktop. On a side note, however, they fixed java in gutsy so groupwise works with 3d desktops now :guitar:

---


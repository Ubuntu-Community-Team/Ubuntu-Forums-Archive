---
title: "Wine Problem"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by happybill on 2006-10-22
I've installed wine.  I know it works because I have managed to install IE6 which works.  (I thought that I would then be able to install and use MS Money - but that's another story).

The present problem is this.  I've installed SolSuite, It is there and worked immediately after installation.  However, after closing it, I cannot restart it.  The link that has been thoughtfully placed on the desktop does not start it, and I cannot start it in the Terminal either. It appears that in the command, "wine ~/.wine/drive_c/Program Files/SolSuite/SolSuite.exe", the space between Program and Files is the problem.
The result is "wine: cannot find '/home/ubill/.wine/drive_c/Program'"

Can anyone tell me what my mistake is?

---

### Post by Anonii on 2006-10-22
> **happybill said:**
> I've installed wine.  I know it works because I have managed to install IE6 which works.  (I thought that I would then be able to install and use MS Money - but that's another story).

The present problem is this.  I've installed SolSuite, It is there and worked immediately after installation.  However, after closing it, I cannot restart it.  The link that has been thoughtfully placed on the desktop does not start it, and I cannot start it in the Terminal either. It appears that in the command, "wine ~/.wine/drive_c/Program Files/SolSuite/SolSuite.exe", the space between Program and Files is the problem.
The result is "wine: cannot find '/home/ubill/.wine/drive_c/Program'"

Can anyone tell me what my mistake is?
The trick here is auto-completion with TAB. Get to /home/ubill/.wine/drive_c/ and then "cd Pro" and hit TAB, it will autocomplete the path for you.

Anyway, you either do that, or fill the gaps like this:

**wine /home/ubill/.wine/drive_c/Program\ Files/SolSuite/SolSuite.exe**

but autocompletion is a great feature especially for command line junkies.

---

### Post by happybill on 2006-10-23
Many thanks Anonii, it did the trick.  Simple when you know how, but I'm struggling up the learning curve.

Next question about wine.
Is it possible to install MS Money to run in Ubuntu?

---

### Post by Anonii on 2006-10-23
> **happybill said:**
> Many thanks Anonii, it did the trick.  Simple when you know how, but I'm struggling up the learning curve.

Next question about wine.
Is it possible to install MS Money to run in Ubuntu?
[http://appdb.winehq.org/](http://appdb.winehq.org/)
will solve all your questions about compatibility in Wine.

From what I see, you cant run MS Money 2007, yet, on Wine (dunno on CrossOver office), which is a commercial application. But you can run MS Money 2006, in CrossOver Office, but not in Wine, from what I see here:
[http://appdb.winehq.org/appview.php?iVersionId=4641](http://appdb.winehq.org/appview.php?iVersionId=4641)

---

### Post by happybill on 2006-11-28
Hello,

Have just seen your last post.  Money 2004 does not work in wine or crossover and crossover tell me there are no plans to make it work.  It might be made to work in crossover with crafty fixes involving bottles, but the instructions for doing this are old.  I am waiting for the formal release of V6.

---


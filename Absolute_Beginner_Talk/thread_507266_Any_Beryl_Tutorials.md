---
title: "Any Beryl Tutorials?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-07-22
I have installed Beryl, thats not my problem.  My problem is I have no idea what half the things do in the Beryl Manager, and that whenever I try and find a tutorial that would explain everything, all I can find are a million tutorials explaining how to install it.

Also, I installed it using Synaptic.  However, most of the tutorials seem to involve multi-step processes involving the terminal.  Did I install it properly/did I install the right thing?  It seemed too easy...

Thanks.

---

### Post by gavintlgold on 2007-07-22
Is the beryl wiki still running? If so, there should be info there.

However, keep in mind that Beryl is no longer under development. Compiz Fusion is a mix of beryl and compiz. Check it out on Opencompositing.org. You can install Compiz Fusion with Trevinho's repo, as well, so it shouldn't be difficult. You'll get much more support if you do that.

If you want, my videos might help too (see my signature).

---

### Post by Yes on 2007-07-22
Ok, I'll look into those.  Also, do I have to restart my computer to get the effects to show up?

Is Emerald an addon to Beryl?

---

### Post by Yes on 2007-07-22
Ok, I think I've figured out why my changes arn't taking effect:  The Window Manager is set to Metacity, but if I try and set it to Beryl, it just resets it back to Metacity.  Why is this?

Thanks.

---

### Post by itisbasi on 2007-12-21
yep....i'm running into the same problem....i was able to get it to work ...the 3D cube and everything....now i somehow seem to be unable to get the cube desktop to work...everything else works....

---

### Post by Sorivenul on 2007-12-21
Since you're on 7.04 and you installed Beryl separately, in terminal try typing:
```
beryl --replace
```
You may still have to restart, but if that seems to make things worse go back to Metacity by:
```
metacity --replace
```
Hope this helps.

---

### Post by tad1073 on 2007-12-21
I would use [forlongs tut.](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) and Amaranth's backport repo.
[Compiz Community Forums](http://forum.compiz-fusion.org/showthread.php?t=5303)

---


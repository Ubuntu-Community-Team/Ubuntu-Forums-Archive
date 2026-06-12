---
title: "Add/Remove &quot;major failure&quot;"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by E.T.Expatriate on 2007-09-02
Just went to Applications > Add/Remove and got the following dire pop-up:

> **Failed to check for installed and available applications**

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

The only part of that I have some idea what to do with is 'sudo apt-get update' so I entered that into the command line and got *this* message"
> E: Type '&#8220;deb' is not known on line 44 in source list /etc/apt/sources.list


So what happened? And how do I fix it? Note, last session I tried installing an SNES emulator based on instructions from [this blog post]("http://blog.clickonline.org.au/2007/05/17/ubuntu-tip-of-the-day-installing-a-super-nintendo-emulator-zsnes/") which failed and, at the time, seemed to otherwise have no negative affect, but which I now gather jimmied something up.

---

### Post by wormser on 2007-09-03
Have you tried the second command recommended?

```
sudo apt-get install -f
```

---

### Post by sumguy231 on 2007-09-03
Did you copy and paste the instructions there or transcribe them? It looks like you may have made an error somewhere, and messed up your sources.list. Open sources.list in a text editor:
```
gksu gedit /etc/apt/sources.list
```
Find the line that says anything like "deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main" and try putting a # in front of it and saving. Then run apt-get update again.

If you still want zsnes, you can get it from the normal repositories anyway, though it *might* be an older version.

---

### Post by E.T.Expatriate on 2007-09-03
> **wormser said:**
> Have you tried the second command recommended?

```
sudo apt-get install -f
```

Yes, to no effect.

---

### Post by E.T.Expatriate on 2007-09-03
> **sumguy231 said:**
> Open sources.list in a text editor:
```
gksu gedit /etc/apt/sources.list
```
Find the line that says anything like "deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main" and try putting a # in front of it and saving. Then run apt-get update again.

That seems to have fixed it, thank you! 'deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main' was the last line in the file by the way and had somehow ended up with a " in front of it instead of #. I don't understand any of the code, but can you give me some idea why that single character made such a difference?

> If you still want zsnes, you can get it from the normal repositories anyway, though it *might* be an older version.
Its not part of Add/Remove, even at the widest possible setting (though I do recall it being there in earlier versions of Ubuntu). I think that's a subject for a different discussion, however.

---

### Post by sumguy231 on 2007-09-03
The # tells it to ignore everything after it on the line - it doesn't matter what you put there, it won't even look at it so there won't be an error.

Add/Remove doesn't have all of the packages available - use Synaptic and make sure to add the 'multiverse' repository to get zsnes.

---

### Post by Celegorm on 2007-09-03
The # at the start of a line turns that line into a comment as opposed to code that is actually used by the computer. Also try looking for zsnes in synaptic. I find that add/remove does not have as complete a list of applications as synaptic.

edit- apparently I am a very slow typist

---

### Post by sumguy231 on 2007-09-03
By the way, you can enable multiverse and more from the 'Software Sources' dialog.

---

### Post by E.T.Expatriate on 2007-09-03
As suggested, I just used Synaptic to install ZSNES, but there are some issues. Since this is no longer related to the original subject, I've started a new discussion [HERE]("http://ubuntuforums.org/showthread.php?p=3302750#post3302750").

---


---
title: "new flash plugin today - but still no sound"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-12-14
I have been living with the lack of sound from flash since Feisty.  I am now on gutsy, and today a new flash plugin non-free was delivered in the updates.  I was really hoping it would now work - but nope.

In the past I have installed alsa-oss as one workaround suggested and edited firefoxrc to use aoss, nothing works.

So what's the latest fixes.  Anything new that might get it to work?

---

### Post by mkoyle on 2008-01-15
You know, that seems to result from a ... improperly configured update back there between edgy and feisty.

Sometimes getting rid of your sound configuration file works.  The following command moves the file to a new name.  The next time your system tries to access it, it cannot find the file and will create a new, default one.  (I copied this from [http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)).

 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

Does that fix it for you?  If not, we can look for other options.

--Matthew

---

### Post by ubnewbie2 on 2008-01-16
Those files do not exist.

---


---
title: "Can't compile anything"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by endlesssnowfall on 2007-04-09
I can't compile anything from source because whenever I run make, I get this error message:

> libtool: link: `/usr/lib/gcc/i486-linux-gnu/4.1.2//libXrender.la' is not a valid libtool archiveI've tried the suggestions in this thread, [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=238449](http://ubuntuforums.org/showthread.php?t=238449)[/COLOR], but it doesn't help.
What else should I try?  It's a little annoying that I have to wait for .deb packages instead of being able to compile from source immediately.

---

### Post by kvonb on 2007-04-09
Unfortunately due to space constraints on the CD, the compile systen has to be installed seperately.

Either search in synaptic for the following packages or from a terminal run:

```
 sudo apt-get install build-essential gcc-3.4 linux-headers-$(uname -r)
```

(just copy and paste it!)

Then try again :)

---

### Post by endlesssnowfall on 2007-04-09
Thanks, even though I already had these two packages installed, I tried reinstalling them, but compiling still gives me the same error message.

---

### Post by endlesssnowfall on 2007-04-12
I'm still at a loss here, I've tried re-installing libXrender, libXrender-dev, libtool, libcairo2, but nothing has worked.

I used to use Quinn's repository for Compiz awhile ago, which is what probably broke this, but none of the fixes recommended have worked yet.

Any other suggestions?  Not being able to compile anything sucks.

---

### Post by kvonb on 2007-04-13
I'm at a bot of a loss here.

A few suggestions though:

Have a look in /usr/lib/gcc/i486-linux-gnu/4.1.2/ and see what files are in there.  I included a screenshot of what is in mine.

Also, that error message you gave in your original post, notice the double forward slash:

			 				libtool: link: `/usr/lib/gcc/i486-linux-gnu/4.1.2//libXrender.la' is not a valid libtool archive
                                                                ^

maybe that is a clue?

Another suggestion is to completely remove then re-install all the compiling stuff, ie build essential and gcc.  Do it through synaptic, and maybe search for libtool as well.

Regards, Kev :)

---

### Post by endlesssnowfall on 2007-04-13
I tried reinstalling build-essential and gcc, but it didn't help.

My /usr/lib/gcc/i486-linux-gnu/4.1.2/ folder has the same files as yours does, plus some other ones as well.

I noticed the double forward-slash as well, do you know why that is or where I can fix that?

Thanks for all the help so far.

---


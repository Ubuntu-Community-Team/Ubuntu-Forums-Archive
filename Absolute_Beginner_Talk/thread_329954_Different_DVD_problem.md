---
title: "Different DVD problem"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by ukemike on 2007-01-02
For the most part I have DVDs working just fine, BUT...  There are several DVDs that consistently fail to play all the way through.  My son loves Harry Potter, and the DVD for the Chamber of Secrets consistantly hangs at the same scene.  The error message says something to the effect of, "are you trying to play an encrypted DVD without libdvdcss?"  Obviously I have that installed (used automatix).  I've gotten used to restarting the DVD and then selecting the following scene, and usually all is well.  An odd thing happened last night.  About 40 min into the movie (much earlier than normal) it stopped with the same error.  I restarted it and went to the next scene.  A few minutes later it hung-up again.  This pattern repeated until I got sick of it and told my boy that we couldn't watch the movie because it was broken.  I have one or two other DVDs that typically fail to play all of the way through. 

I use totem to play the DVDs, I have edubuntu 6.10, and used automatix to install the various codecs.

Any thoughts?

---

### Post by arnieboy on 2007-01-03
do two things:
1)
```
sudo apt-get install totem-xine
```
to make sure totem-xine is installed (and totem-gstreamer is uninstalled)
and 
2) The DVD isnt scratched (play it in windows or elsewhere to check)

---


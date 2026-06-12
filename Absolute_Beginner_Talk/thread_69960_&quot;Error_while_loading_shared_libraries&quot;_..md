---
title: "&quot;Error while loading shared libraries&quot; .. please help"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by BigNeonGlitter on 2005-09-28
I am trying to run an exectuable called ibm5250 by doing a "./ibm5250" and I am getting a reply stating: "Error while loading shared libraries: libXm.so.3: cannot open shared object file: no such file or directory exists". I have researched a bit and found that I need to load OpenMotif, which I did, but I still get the same message. I have searched IBM's support documents, but found nothing, so I thought I'd ask here. I will further add that I am a newbie at all this, so I apologize if I am missing something obvious here. Thanks!

---

### Post by mlomker on 2005-09-28
Download **libmotif3** using Synaptic.

---

### Post by BigNeonGlitter on 2005-09-28
Thanks for the reply .. I did as you said, but I still get the same error. It seems to me (and remember, I'm a Windows guy that knows nothing about Linux) that it's a path type of issue. Like "/opt/ibm/iSeriesAccess/bin' executables cannot resolve to whereever this shared library is supposed to be. Could that be it?

---

### Post by mlomker on 2005-09-28
I don't know.  You didn't post the exact error message and I'm not familiar with this program or its dependencies.  Usually there's a README file explaining the components that you have to have in place.

---


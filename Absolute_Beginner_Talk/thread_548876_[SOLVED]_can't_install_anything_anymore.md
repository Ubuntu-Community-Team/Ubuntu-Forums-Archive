---
title: "[SOLVED] can't install anything anymore"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Concentrate on 2007-09-11
Ok, so I can't install anything using the synaptic package manager or the command apt-get. I tried to install a new language too, but it said it failed. I can still surf the internet (this is the computer with the problem) but when I try to install something from the synaptic package manager, it tells me: 
"Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10), connection timed out"

I've recently successfully installed compiz-fusion and envy if this has anything to do with that, but I wouldn't know cuz I'm a complete noob. This is my second time playing with linux and I'm still learning.

---

### Post by reckless2k2 on 2007-09-11
ping one of the other servers. i remember there was a server issue recently and you might just have to fix your locations in the sources.list.

---

### Post by danny joe ritchie on 2007-09-11
I'm a newbie too! Sounds like a problem from the other end,but I could be wrong!
Hang around here and somebody will have an answer!

---

### Post by llamakc on 2007-09-11
You can either wait for the ca.* archives to come back available or manually edit /etc/apt/sources.list (make a backup copy FIRST!) and remove the "ca." from each line so they all begin like:

archive.ubuntu.com

instead of ca.archive.ubuntu.com

---

### Post by Concentrate on 2007-09-11
thanks so much for the fast help guys. I replaced all the ca's and it worked. Sorry for wasting your time with such a simple fix. I'm starting to enjoy ubuntu more and more, and I know I'll be running into more problems later down the road, so look forward to answering a whole bunch of questions :D

---

### Post by reckless2k2 on 2007-09-11
your problem is not a waste. that's what we are here for. 
enjoy. don't be afraid to ask.

---


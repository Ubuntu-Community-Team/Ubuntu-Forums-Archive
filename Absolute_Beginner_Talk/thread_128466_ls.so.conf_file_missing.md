---
title: "ls.so.conf file missing"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by alexd0909 on 2006-02-11
Hi there, 

While I was trying to build Xine, I noticed that /etc/ld.so.conf was missing. I wasn't able to get very far after that: the xine-ui ./configure failed after it could not find xine-lib. 

This seems to me rather serious. Can anyone help me to figure out what happened to ld.so.conf? Thanks.

---

### Post by TeeAhr1 on 2006-02-11
I don't know what that file is/does, but a quick search through my filesystem shows that I don't have it either.  When you were building Xine, did it keep going after realizing that the file wasn't there?

---

### Post by alexd0909 on 2006-02-12
ld.so.conf is a file that contains a list of directories that is used by ldconfig to create links to shared libraries used by the run-time linker. See man ldconfig for more.

Anyway, after reading a couple other threads on the same topic, I decided to create an ld.so.conf file with /usr/local/lib (that's where xine-lib installs by default). I then started to build the xine-ui component. It looks like it found the xine-lib alright but it failed to find several other dependencies. 

I'll slog through it, an error at a time. I'm not discouraged but I find it hard coming from the Windows World where everything pretty much works right out of the box. I've been frustrated before with other Linux distros and have given up out of impatience and laziness. That's not something I'm proud of.

It seems to me that the difficulty is cultural. I imagine that my frustrations with Linux are probably similar to those of an English North American moving to Continental Europe: Different and difficult at first but hopefully worth it.

---


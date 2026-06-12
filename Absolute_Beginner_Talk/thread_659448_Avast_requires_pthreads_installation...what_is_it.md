---
title: "Avast requires pthreads installation...what is it?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-05
My version of Avast! Anti-Virus requires installation of pthreads.  What are they?  How do I make sure they are installed?  If they are not installed, how do I install them, please?

---

### Post by rubicon on 2008-01-05
pthreads is an implementation of threading mechanism in UNIX. Full name is POSIX Threads.

If you have libc, then you have pthreads. Tip: all C and C++ programs depends on libc.

---

### Post by jhvillegas2 on 2008-01-05
How can I tell if I have libc installed (it is "installed", isn't it?).

---

### Post by rubicon on 2008-01-05
As you know (well, I suppose you do :) ) linux kernel is written in C. All system tool written in C. Some in C++. What they are depend on?

Um. Go into Synaptic and find package 'libc6'.
[COLOR="Silver"]
PS: Don't mind me riddling. Sometimes I'm intolerable.[/COLOR]

---


---
title: "what does this mean"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-10-05
so i was trying to get my bluetooth dongle to work, I had it working in edgy no problem by the way, and iwas going about it in my usual way in trying to figure things out in linux.  Trial and error.  well i ended up having to do one of these sudo apt-get install -f
and now when i go to installl build-essential i get this:

 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed

how do i make this go away???

---

### Post by borris.morris on 2007-10-05
try "sudo apt-get install build-essential", that should make the whole thing go away (it installs g++)

---

### Post by endlessurf on 2007-10-05
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

---

### Post by tgalati4 on 2007-10-05
Welcome to package dependency Hell.  It's sometimes easy to fix.  Sometimes it destroys your machine.  Welcome to the bleeding edge.

>sudo apt-get install libc6-dev

Keep installing stuff until the dependency errors go away.  As a general rule, you will need *-dev packages for most things that you custom build.  Don't be discouraged.  Just keep installing and compiling until one of the following conditions is satisfied:

1) You have a working package!

2) You decide to quit after installing 13 packages and you are still getting compile errors.

---

### Post by macogw on 2007-10-05
He's not reporting compile errors, guys.  What's with the responses in this thread?  He said apt's not getting build-essential's dependencies.  I think a server was down a bit ago.  It might be back up.  Original poster, has the status changed?

---

### Post by tgalati4 on 2007-10-05
I'm answering his next question.

---


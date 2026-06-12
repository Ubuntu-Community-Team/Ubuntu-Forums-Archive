---
title: "Java install problems"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by TheRisingTyrant on 2007-11-17
I have installed a fresh copy of Gutsy Gibbons and java won't install. I go into the Add/Remove programs and install it that way and it comes up with the error message;

Cannot install 'sun-java5-bin'

This application conflicts with other installed software. To install 'sun-java5-bin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I then went to the synaptic package manager and tried to install it that way and I got this error

sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
 	ia32-sun-java6-bin (=6-03-0ubuntu2) but it is not installable

I have installed 3 fresh copies of Gutsy Gibbons and it come up with the same error every time.

Thanks in advance.

---

### Post by Inxsible on 2007-11-17
Wait a minute !!

Why are you trying to install java 5 when you already have java 6 installed ?

---

### Post by TheRisingTyrant on 2007-11-17
Because thats the one in Add/Remove programs and when I go to the terminal and type in 'java --version' it says that there is no version of java installed

---

### Post by rsambuca on 2007-11-17
You need to activate all of your repos first.  Go to "System -> Administration -> Software Sources" and check all of the repos.  Then reload the repositories and you will be able to install.

---

### Post by TheRisingTyrant on 2007-11-17
I'm afraid that still hasn't worked:(
It's still the same errors coming up.

---

### Post by ntu on 2007-11-17
I just went to utube, clicked on a video and then on the ff plugin required and  it installed what I needed - I think it was java.

---


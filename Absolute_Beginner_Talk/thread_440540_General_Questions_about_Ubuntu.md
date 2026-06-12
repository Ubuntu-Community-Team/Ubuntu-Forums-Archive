---
title: "General Questions about Ubuntu"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by danmpem on 2007-05-11
Hi, I'm new at Linux, and I just have a few questions about my Ubuntu system. I'm running Ubuntu 7/KDE on a Dell 2.4 GHz/1 GB RAM/Dual Boot w/ Windows XP.

On the terminal:

1. How may I get a masterlist of all my packages installed?

2. How may I find out all the man pages I have? Meaning, if I want the man page for Evolution, but let's say I don't exactly what to put after "man" in the terminal, how do I find out?

3. How do I get a masterlist of all the packages in my repositories?


In KDE:

4. How do I get my system to stop asking me for the root password every time I want to open any program that has to do with system files, networking, etc.?

Thanks!

---

### Post by Dr Small on 2007-05-11
> **danmpem said:**
> Hi, I'm new at Linux, and I just have a few questions about my Ubuntu system. I'm running Ubuntu 7/KDE on a Dell 2.4 GHz/1 GB RAM/Dual Boot w/ Windows XP.

On the terminal:

1. How may I get a masterlist of all my packages installed?

2. How may I find out all the man pages I have? Meaning, if I want the man page for Evolution, but let's say I don't exactly what to put after "man" in the terminal, how do I find out?

3. How do I get a masterlist of all the packages in my repositories?


In KDE:

4. How do I get my system to stop asking me for the root password every time I want to open any program that has to do with system files, networking, etc.?

Thanks!
First off, you really don't want it to stop asking you for the root password. That would be insane! Think of the possibilities it would leave open for you to mess things up!

Secondly, I think you can browse all of the installed packages with Synaptic, or aptitude.

Dr Small

---

### Post by jputman01 on 2007-05-11
definitely dont want to get rid of it asking you for root password, something really bad could happen (could i be any more vague but direct at the same time???)

browse all your pacakges you have with synaptic:)

---

### Post by freakavoid on 2007-05-11
"dpkg --get-selections" for the first one.

---

### Post by carlosqueso on 2007-05-11
for number 3, use a nifty command called apropros (I think that's how it's spelled) and type 
```
apropros <thing you're searching for>
```  It searches the man pages for the string. Try general terms to get more results. Of course, you could always just try man <thing you think>, it won't hurt anything.

Also, if you don't want to browse synaptic, you can always search [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for the complete contents of the ubuntu repos.

---


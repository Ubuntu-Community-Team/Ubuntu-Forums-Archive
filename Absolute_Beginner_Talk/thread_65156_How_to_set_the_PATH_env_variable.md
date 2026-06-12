---
title: "How to set the PATH env variable?"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by Oystein on 2005-09-13
I've downloaded and installed the standard Linux binary self-extracting version of Java 5 from Sun's site, to a subdirectory of my user home directory, and I'm trying to tell bash to find the binary files there (javac etc.)

First I edited the PATH variable in .bash_profile in my home directory by including a line at the end:
PATH="/home/myusername/Java/jdk1.5.0_04/bin:${PATH}"
but the system could not find programs in the bin directory. Using ~/Java... doesn't work either. I've also tried editing /etc/profile as root, but even after that, the env command shows no change in PATH (after starting up a new shell or even relogging, of course). I can run the files manually by typing in the whole pathname, so they're there all right, I just can't change PATH. Am I missing something obvious here?

Oystein

---

### Post by ebrowne on 2005-09-13
Do you have export PATH at the end of the .bach_profile?

---


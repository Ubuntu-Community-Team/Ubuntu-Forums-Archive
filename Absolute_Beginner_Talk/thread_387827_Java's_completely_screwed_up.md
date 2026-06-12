---
title: "Java's completely screwed up"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2007-03-18
Ok, I tried removing java via the package manager gui; couldn't do it, tried an aptitude purge, couldn't do it, said I'd have to manually remove java, so I deleted all the files in /usr/share/java and /usr/share/java-common

Java is still "on" my machine, how do I get rid of it?

Trying to purge it now can't find the files and the gui package manager says: E: sun-java5-bin: Package is in a very bad inconsistent state - you should

Please help!

---

### Post by annda on 2007-03-18
probably the best idea would be to find any leftover java files and remove them manually:

sudo updatedb
locate java

and get rid of them all.

---

### Post by Majin Zero on 2007-03-18
I also now get this anytime I try to do anything with my packages:

Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by annda on 2007-03-18
are you running multiple instances of apt-get / aptitude / synaptic? that would explain the "couldn't lock" error message.

---


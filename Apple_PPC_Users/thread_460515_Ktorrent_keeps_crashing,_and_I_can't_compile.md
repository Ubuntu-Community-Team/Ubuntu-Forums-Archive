---
title: "Ktorrent keeps crashing, and I can't compile"
date: 2007-05-31
forum: Apple PPC Users
---

### Post by sldonmtns on 2007-05-31
I'm running Kubuntu on a mac mini, and Ktorrent (2.1 from the repositories) keeps crashing. It runs for an hour or two then the program crashes.

So I tried compiling the latest beta of ktorrent, but I get the following error:
```
checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev.

```

I have libstdc++6-4.1-dev installed.

So, I am wondering if there is any way I can get ktorrent to work properly.
A tracker I frequently use doesn't allow deluge, so I need to stay with ktorrent.

Thanks for any help

---

### Post by stmiller on 2007-05-31
And this is on Feisty (I assume)? Ktorrent 2.1 works ok here. 

Have you installed the 'build-essential' convenience package?

apt-get install build-essential

Might try seeing if there are issues with this release on the ktorrent forum.

---

### Post by sldonmtns on 2007-06-01
Thanks, that worked. The beta ran all night without crashing, so my problems should be fixed now.

---


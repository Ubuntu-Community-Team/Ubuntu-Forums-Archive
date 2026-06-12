---
title: "Problem installing gnucash-2.0.4"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by thornmastr on 2007-01-08
I am trying to install gnucash-2.0.4. I downloaded the tar file and uncompressed it. When running the ./configure I found the following problem.
"library requirements (libgnomeprint-2.2  libgnomeptintui2.2) not met.

Using synaptic, I found that libgnomeprint2.2-dev was installed but libgnomeprintui2.2-dev was not installed so I attempted to install it. I got the following errors:

The following packages have unmet dependencies:
  libgnomeprintui2.2-dev: Depends: libgnomeprintui2.2-0 (= 2.12.1-4) but 2.12.1-4ubuntu2 is to be installed
E: Broken packages

At this point, I need some help. Fist of all, what is this trying to get me to see. I know that synaptic has a "fix broken package" option and I used that. I do not know what that did but it certainly was fast and appeared to accomplish nothing because it did not resolve the problem.

Suggestions and ideas to resolve this problem are most welcome.

Ubuntu 6.10. Using IceWM.


Thank you,


Robert Berman

---

### Post by Efwis on 2007-01-08
make sure all your repos are available, you can use synaptic to check this in synaptic click on settings>repositories and make sure everything has a check next to it. 

next open terminal and do the following
```
sudo aptitude update
sudo aptitude install libgnomeprintui2.2-dev
```

This will install the libgnomeprintui2.2-dev file and all of it's dependancies. if you still get an error, then I would suggest using synaptic or aptitude to install gnucash from the repos. albeit the version in the repos is not 2.0.4.

---

### Post by hal10000 on 2007-01-08
If you have universe (and/or multiverse) repositories, you can install gnucash with: [COLOR="Red"]sudo apt-get install gnucash[/COLOR]

---

### Post by thornmastr on 2007-01-08
Efwis, your solution worked very nicely.

Thank you,

Robert Berman

---

### Post by Efwis on 2007-01-08
your welcome,

Glad I could help.

---


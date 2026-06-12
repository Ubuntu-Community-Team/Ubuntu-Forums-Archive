---
title: "Wine Dependancy error! need help!"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Fuzzban on 2007-03-19
So, In the prosses of installing wine using:
        sudo apt-get install wine (after i did the update)

I got this:

  justin@justin-desktop:~$ sudo apt-get install wine
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.
 
  Since you only requested a single operation it is extremely likely that
  the package is simply not installable and a bug report against
  that package should be filed.
  The following information may help resolve the situation:

  The following packages have unmet dependencies:
    wine: Depends: libgphoto2-2 (>= 2.3.0) but 2.2.1-2ubuntu4 is to be installed
          Depends: libgphoto2-port0 (>= 2.3.0) but 2.2.1-2ubuntu4 is to be installed
  E: Broken packages

What the hell do i do?

---

### Post by zvacet on 2007-03-19
synaptic>edit>fix broken packages
Why didn´t you install wine from synaptic?

---

### Post by Fuzzban on 2007-03-19
It said the same thing when I tried too.

---

### Post by PatheticMoFo on 2007-03-19
I was having the same problem and found this:
[http://www.ubuntuforums.org/showthread.php?t=387824](http://www.ubuntuforums.org/showthread.php?t=387824)

The 5th post gives the answer

---


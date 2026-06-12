---
title: "Where to install programs?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-30
I want to install jGrasp, an IDE for Java but it isn't in the repos.  The instructions from the website are this:

Unzip the distribution (.zip) file in the directory where you wish to install jGRASP. This will create a jgrasp directory containing all the files. You may want to add the "bin" subdirectory of this directory to your execution path or create a soft link to .../jgrasp/bin/jgrasp from a
directory on the executable path.

What directory do I want to install jGrasp?  Should I install it in my home directory or elsewhere?  

Also, for anyone with any experience in this, will jGrasp automatically see my JDK installation?  It does on Windows, but I don't even how Windows installed anymore so if I can't get jGrasp working then my data structures class is gonna be a little hard than norma :-p  Any help?

---

### Post by jpk on 2007-10-30
hi,

You can install anywhere you'd like, but I recommend that you put all non-distribution sofwtare in /opt if you have access to that. Then make a symlink or add it to the path, as their website suggests.

---


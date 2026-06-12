---
title: "cvs and svn?"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by ecto on 2006-01-30
How would a person use cvs or svn? Everytime I asked someone how they got fluxbox or openbox people tell me "I used cvs/svn". I would like to know how to use this (this would make a great how to especially for beginners :D)

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=ecto]How would a person use cvs or svn? Everytime I asked someone how they got fluxbox or openbox people tell me "I used cvs/svn". I would like to know how to use this (this would make a great how to especially for beginners :D)[/QUOTE]
Well, what they really mean is that they installed the program from source.

CSV and SVN (Subversion) are tools used by software developers used to track revisions (changes) to the software.  CVS has been around a long time, but Subversion has been designed as a replacement that improves on some of the weaknesses of CVS.

The general idea in many open source projects is that the developer publishes the source code on the web for others to download, compile, try out, test, submit modifications, etc.  CVS or SVN let the people interested in the project track the source code at any given moment.  

So if you feel you really want some new feature that hasn't been tested very much yet and built into a stable release, you can grab the latest source code from the developer's published repository.  This doesn't always lead to the best results.  Sometimes developers check-in code that will not compile cleanly on different setups, or there may be critical bugs, etc.

Once a project becomes more stable, pulling the latest CVS or SVN can still get you minor bugfixes or features that may take some time to make it into a general release.

To get the software, you use the appropriate client (cvs or svn).  There are some nice graphical clients for beginners, too.  I find RapidSVN to be pretty convenient to use at times.

Here, for example, are SourceForge's instructions for using their relatively new Subversion service:
[http://sourceforge.net/docs/E09/en/#top]("http://sourceforge.net/docs/E09/en/#top")

Once you get the source, compiling and installing is a whole sepreate issue.  See this guide:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

Even though there is no tarball in the case of pulling from CVS or SVN, you would basically still be building from source.

This is admittedly a lot to take in all at once, but I hope I explained the general idea well enough.

---


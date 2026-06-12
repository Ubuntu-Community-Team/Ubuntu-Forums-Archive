---
title: "Using Open SSL within C [question]"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2008-04-04
Before I talk about my problem I would just like to thank the ubuntuforums.org community.  You guys have been great, helping n00bies like myself get adjusted to ubuntu.  Without your support, I would still be using windows xp.  Thank you.

I am working on a programming project that involves C and open ssl.  What packages do I need to install/configure?  I have access to a unix server with open ssl set up, but I would rather do everything locally.  This is how I have been compiling on a solaris system:

gcc des5.c -o des -lcrypto -I/usr/local/ssl/include -L/usr/local/ssl/lib

Also I am working via command line about 6 folders deep from the home directory:
baka@baka-desktop:~/Documents/College/University/Security/project2$ 

Its just very annoying to see that line take up half of the command prompt.  Is there anyway to shorten it?  IE: baka@baka-desktop: ~/project2$

---

### Post by Hospadar on 2008-04-04
well you could move the project to your home folder, or make a link in your home folder and use that.

You'll need to install libssl and libssl-dev I would think.  Then when you compile, all you should need to do is add a -lssl flag (that's a lower case L) to whatever other compiler flags you might be using

To create a link, do something like ```
ln -s ~/Documents/College/University/Security/project2 proj2_link
``` and then you can "cd ~/proj2_link"

---


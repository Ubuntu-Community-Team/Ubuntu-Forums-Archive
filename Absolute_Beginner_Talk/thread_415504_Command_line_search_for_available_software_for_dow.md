---
title: "Command line search for available software for download"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by aleska on 2007-04-20
Whenever I want to install some program, like synergy for example, I always want to check to see if it is in the repositories I've included in my sources.list file.  When I was running ubuntu before, I used to launch synaptic package manager and search for it there.  Now that I'm using kubuntu, I've been going to Add/Remove Programs and doing a similar search.

How inefficient, right?

How do I search from the command line, to see if a package is available for download through my repositories?  What if I don't know the programs full name, I just know it starts with, or contains some text (e.g. programs that have the text "smb" somewhere in its name).   

While I'm at it (asking questions that is), how from the command line would I search/confirm what programs I've already installed? 

Many TIA!
-aleska

---

### Post by lamalex on 2007-04-20
apt-cache search <package>

---

### Post by LaRoza on 2007-04-20
To see if you could install a program through the command line, just try and if it doesn't work the answer is no, if it does work, the answers yes.

Most programs are located in /usr/bin, I believe, so searching there would tell you what you have.

Actually, anything called bin holds programs (binary)

---


---
title: "Apt-get update failure"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-05-12
What is happening to Ubuntu?

Using cut & paste at:

[http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

for

Install Sun Java

I sudo'd apt-get install fakeroot. It returned many lines of text about "couldn't stat". It also said, run apt-get update.

Sudoing that returned:

W: You may want to run apt-get update to correct these problems
E: Couldn't find package fakeroot
mark@lexington:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by testube_babies on 2006-05-12
Make sure you have extra repositories enabled:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Then I would recommend installing Java from this how-to (at the bottom of the page):
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Mark_in_Hollywood on 2006-05-12
Synaptic shows Multiverse and Universe are "checked". Just to be sure, I "reloaded" the repositories.

Received the same error message about 'couldn't stat'.

 What else could this be?

---

### Post by mostwanted on 2006-05-12
[QUOTE=Mark_in_Hollywood]
mark@lexington:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/QUOTE]

Remember: it's *sudo* apt-get update and remember to close down Synaptic before issuing this command (or you could just do the humane thing and do it right from Synaptic - graphical apps need love too!).

Edit: BTW, do other packages download? It could be that the repos are down.

---


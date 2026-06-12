---
title: "VMWARE installation and some"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by mandrakeghost on 2005-11-27
i know i am still a whole stupid with this ubuntu thing. i am trying to learn everything,,, i feel like a new born baby...

just want to ask... about vmware installation

i was installing it already and everything was going well when i got to installation of manual ... 

The path "/lib/vmware" does not exist currently. This program is going to createit, including needed parent directories. Is this what you want? [yes]

In which directory do you want to install the manual files?
[/man] /man

The path "/man" does not exist currently. This program is going to create it,
including needed parent directories. Is this what you want? [yes] 

Unable to get the access rights of source file "./man".

Execution aborted.

it's simple i know...but i really don't know. tell me what to do...
thanks

and...i'd also like to know how to connect to printer of windows network


hope to befriends with u all

---

### Post by MartinG on 2005-11-27
It looks like you're installing as the ordinary user? You need to install as root (sudo <install command>

---

### Post by mandrakeghost on 2005-11-27
i used sudo...

i am still getting it

---

### Post by MartinG on 2005-11-27
Checking my copy of vmware (version 5.0.0-13125), it installs the man file in /usr/share/man, not in /man.  Accordingly, there is no file in the installer to go into /man (which is in any case AFAIK not part of a standard Linux file system).  This means that the message you get is in fact saying there is no source file, and not, as it seems at first sight, that it can't get at the source file.

I wonder why your installer suggests /man? Why don't you try again but give a path of /usr/share/man in response to the question, and see what happens?

---


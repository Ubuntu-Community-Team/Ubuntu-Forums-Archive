---
title: "Help!  I've hosed my kicker"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-09-05
I'm running Kubuntu 6.06.1 with kbfx installed.
 
I was fiddling with the K menu and now the kicker constantly crashes.
I've restarted X several times to see if that would fix it, but each time the kicker crashes immediately.
 
The rest of X works fine - I can move between virtual desktops, open applications manually (using ctrl+2) such as konsole and kate, and move windows around without any problems.  It just seems to be the kicker.
 
I think the problem is that I copied and pasted some of the entries in the K Menu to other areas of the K Menu and then gave them an identical name.  For example 'Terminal (Konsole)' became 'Terminal (Konsole-2)' once I copied and pasted it.  I then renamed it from 'Terminal (Konsole-2)' to 'Terminal (Konsole)'.  Therefore, there were two 'Terminal (Konsole)'s in my K Menu.
 
Is there a K Menu configuration file I can edit manually, eg. through Kate?  If so, where do I find it?
 
Alternatively, can I re-install the default K Menu to get around the kicker crashing?

---

### Post by editrix on 2006-09-05
All I can help with is this:

> **n00b@linux said:**
> Is there a K Menu configuration file I can edit manually, eg. through Kate?  If so, where do I find it?
All the KDE config files are text files, in /home/username/.kde/share/config

---


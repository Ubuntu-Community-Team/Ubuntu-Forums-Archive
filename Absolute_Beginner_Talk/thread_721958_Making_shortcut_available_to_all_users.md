---
title: "Making shortcut available to all users"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by PhrygianCat on 2008-03-11
Is it possible to make a shortcut to an app on the desktop and make it so that any users logging to this computer be able to see & execute it? I'm a noob and am thinking about doing something similar to putting shortcut in the c:\documents and settings\all users\desktop folder in Windows. Thanks for the help.

---

### Post by spiderbatdad on 2008-03-11
/home/[username]/.gimp-2.4/menurc  is where I think you'll find them. I'm not sure how to share them across all user accounts...you could  become root and copy the file to each users directory. I'm sure a bash script could handle it short and sweet.

---

### Post by PhrygianCat on 2008-03-11
Sorry if  didn't give any details on the scenario. I'm trying to introduce Ubuntu desktop at work as an alternative to Windows. And I've joined the Ubuntu desktop to the domain so that it would be authenticated by the Active Directory.

So now I want to make it so that a shortcut to an app or SMB share folder can be created and made available automatically as soon as a new user (that have never logged in on this computer) logged in. May be via a logon script?

---

### Post by spiderbatdad on 2008-03-11
This might be what you're looking for [http://ubuntuforums.org/showthread.php?t=210142](http://ubuntuforums.org/showthread.php?t=210142)
If not, I'll keep trying. Sorry misunderstood the first post. Thought you were trying to make common keyboard shortcuts for all users.lol.

---

### Post by gobuntu on 2008-03-11
Phrygian Cat.

First of all, why need a short cut to applications, if we have already the "Applications" drop down menu?

If SuperUser wants all other users to have certain shortcuts on their desktop, he could copy all those shortcuts to individual Desktops, under certain conditions.

A Desktop is a folder, and as such it only shows what it contains, would say.

Do note, though, that links in Ubuntu LINUX are far more than the equivalent of shortcuts in Windows. For instance, in Ubuntu LINUX one can drop objects into a link to a folder, whereas in Windows one can not do so.

Also, copying links is not a straightforward proposition, specially if it involves crossing boundaries, such as users, hard drives, computers, and so forth. Even backups of links is not a closed-eye solution, for they can be copied as files or as links, in Linux.

Linux is VERY SMART on link management, as can be verified when files are moved, removed, renamed, and so on.

---

### Post by PhrygianCat on 2008-03-11
Spiderbatdad, that's helpful, but now how do I set it so that the person logging in after me have the same shortcut on the desktop, even if that person has not yet have a profile on this computer? The thing is that when an Ubuntu computer is joined to a Windows domain, a user can login without having a profile and local account created first.

---

### Post by PhrygianCat on 2008-03-11
> **gobuntu said:**
> Phrygian Cat.

First of all, why need a short cut to applications, if we have already the "Applications" drop down menu?

If SuperUser wants all other users to have certain shortcuts on their desktop, he could copy all those shortcuts to individual Desktops, under certain conditions.

A Desktop is a folder, and as such it only shows what it contains, would say.

Do note, though, that links in Ubuntu LINUX are far more than the equivalent of shortcuts in Windows. For instance, in Ubuntu LINUX one can drop objects into a link to a folder, whereas in Windows one can not do so.

Also, copying links is not a straightforward proposition, specially if it involves crossing boundaries, such as users, hard drives, computers, and so forth. Even backups of links is not a closed-eye solution, for they can be copied as files or as links, in Linux.

Linux is VERY SMART on link management, as can be verified when files are moved, removed, renamed, and so on.
Thanks gobuntu for helping me understand some differences between Linux & Windows shortcut. I guess I'm just trying to see how I can make it easier for people to feel less scared in trying the Ubuntu computer without doing a staff training.

---

### Post by spiderbatdad on 2008-03-11
That's the part I'm unsure about. And I'm sure it's simple once you know how. It may be possible through the gconf-editor>>apps>>nautilus>>desktop by adding the path there, or again a script to copy the path/of/shortcut to each users  /home/*/Desktop. If the right person spots this post, it will become a simple matter, I'm sure. :)  In gconf-editor you might try right clicking a network icon with no value and setting a path. I've never tried it, and only have one account at the moment, but you peaked my curiosity, so I may create another account and try it.

---


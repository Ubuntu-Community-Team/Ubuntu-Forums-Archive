---
title: "Multiple users in Dapper"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-04-15
I want to find out more about how Dapper handles multiple users - for example does an installed program appear for everyone, can different users have different desktop and software settings, all that sort of stuff.

I've been searching the docs, but can't find much out - can anyone give me links to info on multiple users please?

TIA

---

### Post by PurplePenguin on 2007-04-15
If you install something with the package manager, it will be available for all users. 

Different users have different "home" directories, so they can each have customized desktop settings.  Everything that a user does with his or her normal user privileges affects only his or her own directory.  So if I write a letter in OpenOffice, you can log in but won't see it in the document history, for example.

There probably won't be much information out there about multiple users.  Basically, a system with multiple users is the same as a system with one user - the only difference being the number of user home directories.  When you log into a system, you have no idea if there is one user or one hundred users... if you're logged in, everything you do (as long as you're not acting with root privileges, such as installing new software system-wide) affects only you and your directory.

---


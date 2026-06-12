---
title: "[SOLVED] Install Apps in Windows and Ubuntu"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-19
There are a few apps that I need to be able to access from both my OS'es. Now, of course all apps that put registry entries in Windows are out of the question.

The apps that I am talking about are something like Eclipse for example, which I use quite a lot for my work. We simply extract the eclipse into a folder in Windows too.

The point in having the same install for Windows and Linux, is that if i change my 'lookAndFeel' of the app, the same can also be obtained in the other OS without having to change it all over again. It would also save some disk space for what its worth.

I would also like to know if I can install Java SDK 6 such that both OS'es point to the same install

Thanks

---

### Post by Cypher on 2007-04-19
Since Eclipse is a JAVA app, you could just install it on the NTFS partition for Windows to access and then use NTFS-3G in Linux mount that partition and use the same files.

However, I don't believe the JDK will work cross-platform like that. Any compiled program will either have to be run through Wine on Linux or you'll have to use the native Linux version.

Regards

---


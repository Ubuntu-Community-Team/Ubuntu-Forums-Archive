---
title: "WINE Help.  Confirming installation, and then USING it."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by haemphyst on 2007-04-04
OK...  Got all my hardware running JUST the way I like it.  Now,I have gone tothe "Add/Remove..." in the Application menu, and selected WINE for installation.  It asked for my password, downloaded some files, INCLUDING a 9MB file called "wine", and then it did its (I'm assuming) installation.  I don't know what WINE is supposed to look like, whether it will show up as an application or what.  Can somebody help me determine if it is actually installed correctly?

Now, once that issue is addressed/fixed, how do I then install a Winblows application?  Not being familiar at all with installation otherwise in Linux, if it takes a bunch of effort,or commandline stuff, I'll seriously need somebody to literally hold my hand!

Thanks in advance!
--haemphyst

---

### Post by NICU on 2007-04-06
Hello, once you have Wine installed (through Synaptec or any other method) you should run (from the command line) "winecfg" its the configuration utility for Wine.  Most pieces in there are self explanatory.  

To use Wine you simply need to type on the command line "wine nameOfApplicaition.exe" for example if you want to run Setup.exe, go to the directory of Setup and type "wine Setup.exe" and in almost every place I've used it your application will show up and run like normal.

---


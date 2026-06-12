---
title: "free pascal+terminal"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by mafia88 on 2007-10-11
Hi all!
I'm new to ubuntu and im still figuring out how to install programs through the terminal.
Where do I have to search to find out the proper commands on how to open files,directories,tar files,install programs etc.?
Also, I just downloaded free pascal from freepascal.org so as to learn how to programming in pascal for my computer class. However, I have problems when I try to install it through the terminal. Does anyone have any idea on this?

Im sorry for all these questions, i dont know if I have to post them in different forums.

Thank you for your attention:-D

---

### Post by dondos on 2008-03-03
Sorry for taking so long to answer, but I just found your question on this forum. In case your problem is still not solved,these are some simple steps to install fpc:

FreePascal usually comes as a single tar file you have to un-tar yourself, typing 'tar -xvf fpc-2.2.0-i386.tar'.
This creates a few more tar files and an executable script named 'install.sh'. In order to install fpc, type 'sudo ./install.sh' and follow the prompts.

FreePascal also comes as an rpm (not a good choice for Debian-based systems) or even a deb file.

FreePascal is a great tool, open-source, very advanced technologically, has great support, and is suitable for most of your programming tasks. Pascal may not be the most popular programming language of our time, but still has the most elegant and clean syntax. See for yourself.

---


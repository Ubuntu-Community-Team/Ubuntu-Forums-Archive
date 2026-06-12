---
title: "Issues about uninstalling programs."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by kirbyboy on 2007-05-18
Hi, i'm new in Linux(and my english is not perfect) and i have 2 questions about uninstalling programs in Ubuntu:

The first question is about the .run files, i have searched for topic but only found how installing them, not uninstalling.  A friend told me that with deleting the folder the .run created it's done, is it true?, or there may be something more i have to delete? How do i know if only one or more folders where created?

The second it's about something particular, i installed a .package(desmume 0.7, a emulator for ds, from official web, not from the repositories) and first installed the autopackage program.  When i installed the desmume, appeared a menu called 3rd party manager where i could uninstall the desmume, but the button that i have to click to uninstall is always disabled, i tried open the menu with sudo(always told me i needed the system password), and using root account, but it didn't work, the button was dissabled.  Is there another way of uninstalling?

I know my english is not perfect, if you don't understand what i want to say, just tell me and i'll try to write in another way.

---

### Post by spin2cool on 2007-05-18
The easiest way to install/uninstall programs is by using the Synaptic package manager.  (or by using apt-get from the command line)

Also, try searching the forums next time.  This seems to have the answer to your question:
[http://ubuntuforums.org/showthread.php?t=407035&highlight=autopackage](http://ubuntuforums.org/showthread.php?t=407035&highlight=autopackage)

---

### Post by Najand on 2007-05-18
> **spin2cool said:**
> The easiest way to install/uninstall programs is by using the Synaptic package manager.  (or by using apt-get from the command line)

Also, try searching the forums next time.  This seems to have the answer to your question:
[http://ubuntuforums.org/showthread.php?t=407035&highlight=autopackage](http://ubuntuforums.org/showthread.php?t=407035&highlight=autopackage)

It seems he has downloaded and installed non deb packages. He cannot uninstall it using Synaptic for sure.
Well, for uninstalling such packages, your friend was right. You cannot do anything except deleting those files.

---

### Post by kirbyboy on 2007-05-18
I know the existence of synaptic, but the .run i installed was a game to test my nvidia that i downloaded from a web page(world of padman), and the desmume version in sinaptic was 0.6, i just wanted to try the lastest version.  I just don't want to depend in sinaptic for all, allways will be programs that are not in synaptic

I'll try later in my house about the .package, thanks.

---


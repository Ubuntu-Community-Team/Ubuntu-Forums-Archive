---
title: "[SOLVED] sourceforge"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-16
Need opinions please.  Is Sourceforge software ok? can it break Ubuntu? Do the programs contain spyware or virus? Just curious - I found some apps i would like to download and install. Thanks

---

### Post by Redache on 2007-09-16
Sourceforge is a community of software developers and the chances of a virus being present anywhere are 0.5% and even if that happened it'd be sorted sharpish.

With regard to Ubuntu breaking, no it won't break Ubuntu but you will have difficulty uninstalling software if it's not in the Apt Repo's. Try searching for the Software in the Ubuntu Repo's.

Open a terminal and type:

```
 sudo apt-cache search <Program Name> | Search.txt
```

Obviously replacing <Program Name> with the actual name of the program you're looking for.

Then look in your Home folder and go through the text file and see if the program you want is there (There might only be one program choice but this is a precautionary measure if there's a few versions that end up populating the whole bash screen.)

---

### Post by splintercellguy on 2007-09-16
It obviously depends on what software; SourceForge is just a software repository. What apps are you interested in?

---

### Post by Kilz on 2007-09-16
There is a possibility that any software could be a problem. But things I have installed from Sourceforge are usually good. Linux for the most part isn't prone to viruses. To my knowledge only "proof of concept" ones exist that require you to do something stupid, like run as root, then run install commands in the terminal.

---


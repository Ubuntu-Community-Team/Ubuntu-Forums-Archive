---
title: "kynaptic help"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by Phoenix590 on 2005-06-19
Ok, first off I'm relatively new to linux. The only linux I've used before is kanotix, and when I needed to install a package, I used Kpackage to do it. Ok, now that I'm using kynaptic, instead of kpackage, how do I install something form a file? Should I put my .deb files in a certain folder or is there some option I somehow missed for opening .deb files from my hard drive? Is there a way to install packages without kynaptic (like in konsole)?
                                                  Thanks,
                                                 Phoenix

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=Phoenix590]Ok, first off I'm relatively new to linux. The only linux I've used before is kanotix, and when I needed to install a package, I used Kpackage to do it. Ok, now that I'm using kynaptic, instead of kpackage, how do I install something form a file? Should I put my .deb files in a certain folder or is there some option I somehow missed for opening .deb files from my hard drive? Is there a way to install packages without kynaptic (like in konsole)?
                                                  Thanks,
                                                 Phoenix[/QUOTE]

Let me say....kynaptic is a bad copy. Install the original and see how you like it. Put this in the terminal:

> sudo apt-get install gksudo synaptic

run the program with the command:

> gksudo synaptic

---

### Post by chaumurky on 2005-06-19
[QUOTE=Phoenix590]Ok, first off I'm relatively new to linux. The only linux I've used before is kanotix, and when I needed to install a package, I used Kpackage to do it. Ok, now that I'm using kynaptic, instead of kpackage, how do I install something form a file? Should I put my .deb files in a certain folder or is there some option I somehow missed for opening .deb files from my hard drive? Is there a way to install packages without kynaptic (like in konsole)?
                                                  Thanks,
                                                 Phoenix[/QUOTE]
 Yes synaptic is better. To answer your question - yes you can (and in this case particularly) you should use a terminal. Say you're 'file.deb' file is in '/home/username/downloads'. You just go:

'sudo dkpg -i /home/username/downloads/file.deb'

Easy.

---

### Post by ltmon on 2005-06-19
[QUOTE=Phoenix590]Ok, first off I'm relatively new to linux. The only linux I've used before is kanotix, and when I needed to install a package, I used Kpackage to do it. Ok, now that I'm using kynaptic, instead of kpackage, how do I install something form a file? Should I put my .deb files in a certain folder or is there some option I somehow missed for opening .deb files from my hard drive? Is there a way to install packages without kynaptic (like in konsole)?
                                                  Thanks,
                                                 Phoenix[/QUOTE]

You might be interested in [this](http://kde-apps.org/content/show.php?content=23981).

---


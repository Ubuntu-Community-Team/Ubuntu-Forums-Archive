---
title: "terminal error during an install and now update manager wont load"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by antaeus.r on 2007-12-07
i was trying to install some program in the terminal for the first time and obviously something went wrong during the install because the program didn't install and now the update manager is giving me an error saying:

[B]Could Not initialize the package information

a unresolvable problem has occurred while initializing the package information

E:Type "deb' is not known on line 74 in source list /etc/apt/sources.list, E:the list of sources could not be read[/B]

any help would be greatly appreciated

keep in mind that i am a complete NOOB so walk me through everything

---

### Post by simonalpha on 2007-12-07
This sounds like a problem with your sources list. If you could paste the contents of the file "/etc/apt/sources.list", it would help with figuring out exactly what's wrong.
If you open up your terminal,and type in 
```
 gedit /etc/apt/sources.list 
```
and copy that into a post, it would help greatly...
Simon

---


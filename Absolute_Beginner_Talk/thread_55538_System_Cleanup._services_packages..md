---
title: "System Cleanup. services packages."
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by TreeFrog on 2005-08-09
Hi,
Anyone know if there is a way to clean up after messing around. 
I expect that with all the installing and uninstalling and adding dependancies much of my system is now loaded with unnecessary stuff. 
It is mainly the runtime stuff I'm interested in but others could go too I'm sure

For example: 
I have been playing with amaroK. set up loads of stuf that was probably not necessary. Now I want to install only what is necesary to run it. 

Is there a way to clean it up. 
Perhaps a log of whats used and when. Thus if something is not used for 3 days or more I have a good idea I can remove it. 

Perhaps I need to reinstall and start using the Synaptic Package Manager save markings feature.

Any Ideas?

---

### Post by Juergen on 2005-08-09
'debfoster' and 'deborphan' are both packages that help to determine libs and other stuff that isn't a dependency of another package.
Debfoster can even uninstall stuff that is no longer needed, if you want.

Here's a howto:
[http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster](http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster)

---

### Post by KRavEN on 2005-09-14
I also found this while searching around for removing that trash synaptic et all leave when you just do a removal and not complete removal.

```

 #!/bin/sh
dpkg --get-selections "*" | grep deinstall | awk '{ print $1 " purge" }' | dpkg --set-selections
dpkg --pending --remove


```

Just put that in a file, chmod +x the file, and sudo run it

Im quite surprised none of the package tools or dpkg itself have this mechanism built in.

---


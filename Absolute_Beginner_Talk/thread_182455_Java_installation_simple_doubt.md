---
title: "Java installation simple doubt"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-26
I write java classes. the whole thing is installed and runs just fine. My question is how would i be able to run the classes from anywhere in the file system and not just from usr/lib/j2sdk1.5-sun/bin. I mean some sort of easy way to do this must be there. Please tell me how?

javac and java commands are obviously not recognised when run from any other folder.

---

### Post by stevanbt on 2006-05-26
Hi hotbrainz,
I would have thought that if javac and java don't work when you run them from another folder that they're not in the path (type ```
echo $PATH
``` to see the current contents of the PATH).  You should still be able to run them by either:-
typing the full path, i.e. ```
/usr/lib/j2sdk1.5-sun/bin/java
``` or ```
/usr/lib/j2sdk1.5-sun/bin/javac
```, or
adding /usr/lib/j2sdk1.5-sun/bin to the path type ```
export PATH=$PATH:/usr/lib/j2sdk1.5-sun/bin
``` or add the following to your .bash_profile 
```
PATH=$PATH:/usr/lib/j2sdk1.5-sun/bin
export PATH
```

Hope this helps.

Cheers, Steve.

---

### Post by yota on 2006-05-26
I'm not sure I've understood your problem, if not please explain more in detail what error/issue you are experiencing; meanwhile I think that this can be usefull.

You can select wich java and javac are actually called with:
```

sudo update-alternatives --config java

```

The idea beyond that is that when there're more packages that provide the same functionality, a link in /etc/alternatives points to the default one.
So /usr/bin/java is itself a link to /etc/alternatives/java

---


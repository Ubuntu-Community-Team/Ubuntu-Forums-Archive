---
title: "Adding an entry to the beginning of $PATH?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-11-06
I need to add an entry BEFORE /usr/bin in my $PATH variable.  I added PATH=$PATH:/the/directory in my ~/.bashrc file but that appened /the/directory at the end of $PATH.  The idea is that what is in /the/directory must be seen before what is in /usr/bin.  How can I do that?

edit:  Before adding the line to ~/.bashrc, my $PATH variable looked like this:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
After adding the line to the ~/.bashrc, my $PATH variable looked like this:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun/bin
I need the $PATH variable to look like this:  /usr/lib/jvm/java-6-sun/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by dwhitney67 on 2007-11-06
In your ~/.bashrc, add something similar to what you originally posted, but the reverse.  For example:

```
export PATH=/the/directory:$PATH
```

---


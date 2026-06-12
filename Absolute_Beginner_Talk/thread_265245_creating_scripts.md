---
title: "creating scripts"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Toleshei on 2006-09-25
I need to write a script that runs at startup, to remap my keyboard.  I've tried looking this up on google, but everywhere just assumes people KNOW how to write scripts.  I am a complete newb, and connot figure this out.  Any help?

I tried searching the forum, but I don't think I'm using the right keywords.

---

### Post by LotsOfPhil on 2006-09-25
I write my scripts in either the sh shell or the bash shell.
Maybe try here:
[http://www.freeos.com/guides/lsst/index.html](http://www.freeos.com/guides/lsst/index.html)

---

### Post by colo on 2006-09-25
A shellscript in its easiest incarnation is just a succession of comands, as you'd type them into your interactive shell at the command prompt, saved to a file - with the "shebang" (the two characters "#!") and the absolute path to the interpreter, for example, "/bin/bash", at the very first line. You can create those scripts with any UNIX-compatible text editor you wish, vim, nano, gedit, kwrite... all will do. Just do not forget to chmod the file afterwards (`chmod a+x file`), to make it executeable. A typical shellscript might look something like this:

```
#!/bin/sh
echo "I'm a script running right now. My name is $0.";
echo "I'm about to exit with an errorlevel greater than zero now. Goodbye. :)";
exit 1;

```

Hth.

---

### Post by Toleshei on 2006-09-25
Excellent, that worked great! 

Thanks for the help folks!

---


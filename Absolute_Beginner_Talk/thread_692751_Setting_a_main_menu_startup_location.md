---
title: "Setting a main menu startup location"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by JayeD on 2008-02-10
I'm trying to add a new option to my menu but the program I'm running needs to be started from its parent directory else it doesn't start correctly.

ie.
If I type into the terminal
~$ /somewhere/somewhereelse/program
it will start wrong but if I type
/somewhere/somewhereelse$ program
then all is ok.

Thing is, I'm not sure how to do this in the menu command. Any idea?

---

### Post by JayeD on 2008-02-10
k, from the terminal I can do this

cd /somewhere/somewhereelse ; program

and that works, but I cannot put cd into the menu bit because it says it cannot execute the child process "cd"

---

### Post by PeterJS on 2008-02-10
Try creating a simple script that does:
```

#!/bin/bash
cd /somewhere/somewhereelse ; program

```
and then creating a menu entry for the script.

---

### Post by JayeD on 2008-02-10
Yeah, I guess that would work ok. I still would like to know if the startup path can be changed in the actual menu link though.

---

### Post by JayeD on 2008-02-10
k, like I thought, it does work but it would mean having to change the script if the location moved. Anyone know any other way to do it so the link is only in the menu?

I'm not too up on scripting, only about 2 months into using Linux as my main OS, but could I maybe pass a parameter into the script with the startup path, it then cds to it and then runs from there? I may look into that. Sorry, I just like fiddling.

---

### Post by JayeD on 2008-02-10
k, update...

I've written my first script with more than one line as follows

```
if [ -n $* ] ; then
	cd "$*"
fi
echo "Running in $PWD"
```

and it seems to work fine

---

### Post by JayeD on 2008-02-10
hmm, still not working from the menu though. Just nothing happening.

---

### Post by JayeD on 2008-02-10
Fixed it

```
if [ -n "$*" ] ; then
	cd "$*"
fi
echo "Running in $PWD"
```

Wow, I'm learning. Linux does give you a bigger sense of satisfaction than Winblows :)

---


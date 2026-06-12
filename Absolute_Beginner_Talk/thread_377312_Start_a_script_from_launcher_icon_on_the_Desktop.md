---
title: "Start a script from launcher icon on the Desktop?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-03-05
Howdy,

I am trying to make a launcher icon on my desktop that will launch a shell script that I wrote.  How the heck do I do that?  (The shell script requires a password when it runs)

I tried to set up a launcher using these options - 
application 
```
sh ~/DamnNetwork.sh
```

nothing happens when I click on it.  Strange.

Thanks for your help!,
William Howard

---

### Post by kerry_s on 2007-03-05
Put the full path and gksu in the front for root access, make sure it's executable.
example:
gksu /home/you/DamnNetwork <- you can drop the ".sh"

---

### Post by ewankho on 2007-03-05
Is script set as executable?

---

### Post by mcduck on 2007-03-06
> **kerry_s said:**
> Put the full path and gksu in the front for root access, make sure it's executable.
example:
gksu /home/you/DamnNetwork <- you can drop the ".sh"

If the script doesn't need root privileges, there's no reason to use gksu in the launcher :D

Anyway, if the script file is set to executable all you should need is to point the launcher to the script file with full path, no 'sh' or './' needed.

Of course depending on your script you may need to make it run in a terminal.

---


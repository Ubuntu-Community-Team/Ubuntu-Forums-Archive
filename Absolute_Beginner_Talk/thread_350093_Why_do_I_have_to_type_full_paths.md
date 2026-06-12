---
title: "Why do I have to type full paths?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by rich.bradshaw on 2007-01-31
In other distros, if I want to run a program/script I have written, if I am in the folder with it, I can just type the name of it. In Ubuntu, I have to provide the full path to everything, all the time!

How can I revert this behaviour to normal? None of my scripts work, as they assume that files are in the same directories as the script - useful, as I can then move the scripts around to compile various programs...

Any ideas?

Rich

---

### Post by frodon on 2007-01-31
In ubuntu i noticed also this difference compared to the RedHat version i use for my job, in ubuntu if you want to un the script when you aere in the folder where the script is you have to run it like this :
```
./name_of_script
```

---

### Post by ewankho on 2007-01-31
Are you running it as "./scriptname"? maybe your current path is not in the PATH variable thingy.

---

### Post by Tomosaur on 2007-01-31
Check the output of:
```

echo $PATH

```

This should show you the directories the PATH env var is looking at. Normally it only looks at *bin directories, so you need to add dirs to it. Here's what mine looks like:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/local/bin/eclipse/

```

You can probably just copy mine and set it like this:
```

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/local/bin/eclipse/

```
Then your progs should work. You should also add it in your ~/.bashrc file so that it is permenant.

---

### Post by rich.bradshaw on 2007-01-31
My path variable does have all that, except the eclipse part - the things I'm running are in my home directory, but adding that to PATH didn't change anything...

---


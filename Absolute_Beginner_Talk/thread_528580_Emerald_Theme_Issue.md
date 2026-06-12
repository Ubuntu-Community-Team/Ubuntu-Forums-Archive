---
title: "Emerald Theme Issue"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by monkeyFecalToss on 2007-08-18
Running 7.0.4/beryl/emerald themes

My theme never starts win the os loads.  I only can get it to load when doing this...
alt f2   emerald --replace

it loads till i leave my current session

Is there a script i can write to start this command everytime or am i going about this the wrong way

Thank you in advance

---

### Post by Ek0nomik on 2007-08-18
You can add it to your 'Sessions' menu or you can write a script.

**Adding to sessions**

*System/Preferences/Sessions*

// New
*Name*:  Beryl & Emerald Launcher
*Command*:  emerald --replace

Or you can write a **script**:

*Accessories/Terminal*

```
cd ~/

gksu gedit

#!/bin/bash
#
# Startup script to
# boot compiz.
#
emerald --replace

```

Save as:  .emerald.sh

Now you have to make the file executable:

```
chmod +x .emerald.sh
```

Now you want to go back to Sessions, create new, and add:  ~/.emerald.sh as the command.

Now they seem very similar to being the same thing, but by using a shells script, you could add a lot more commands into one session entry.

---


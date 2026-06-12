---
title: "software problem"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by pafire on 2007-01-15
I am trying to load software from the ADD/Remove Applications, and get the following error message.      E: dpkg was interrupted,you must manually run dpkg-- configure-a to correct the problem.  I am a newbie to Ubuntu, can someone explain this error message

---

### Post by meng on 2007-01-15
Try opening a terminal and typing:
sudo dpkg --configure -a
(enter your user password when prompted)

Then close the terminal and try installing software again.

---

### Post by NeoLithium on 2007-01-15
Open up a terminal window (Applications -> Accessories -> Terminal)
then type:

```

sudo dpkg --configure -a

```

That should be able to fix your problem.  Just means that when something was being done by the package manager, it was interrupted and didn't configure a program properly, so it's asking you to run that to fix the problem manually :)

---

### Post by scrooge_74 on 2007-01-15
really don't know but I dont use that add/remove app. Better try synaptic for adding or deleting software you are going to like it a lot more

try opening a terminal window and do sudo dpkg--reconfigure-a

---

### Post by meng on 2007-01-15
> **NeoLithium said:**
> Open up a terminal window (Applications -> Accessories -> Terminal)
then type:

```

sudo dpkg --configure -a

```

That should be able to fix your problem.  Just means that when something was being done by the package manager, it was interrupted and didn't configure a program properly, so it's asking you to run that to fix the problem manually :)

NeoLi: Are you and I just going to keep competing for the rest of the night to see who gets in answers first?

---

### Post by NeoLithium on 2007-01-15
> **meng said:**
> NeoLi: Are you and I just going to keep competing for the rest of the night to see who gets in answers first?

I was thinking about it; I have tons of coffee ;)

---

### Post by meng on 2007-01-15
NL: Bring it! (your game I mean, you can bring coffee too if you want)

---

### Post by pafire on 2007-01-15
After going to the terminal screen and typing the command, I was prompted for my password. After entering my password I got command not found message

---

### Post by meng on 2007-01-15
Sounds like you typed it incorrectly:
sudo dpkg --configure -a

---


---
title: "Can't add or remove any programs (solution found)"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by jnewm on 2007-08-17
Hi, I'm totally new to linux and ubuntu, so I have no idea where to post this, i.e. whether it's a bug or whether I should be in a different forum.  However, I thought it might be helpful to others if I posted this somewhere, so here goes...

 I was recently using <sudo apt-get install> to install some programs, and all of a sudden I started receiving the following error message:
<segmentation fault (core dumped)>

From then on, I couldn't install anything, and when I tried to start the package manager from the pull-down menu, it would start loading then just stop and close (never reaching the point where it lists the programs available).  Trying to run the synaptic package manager from the terminal didn't work either (I think the error was <warning: could not initiate dbus> or something like that).

Somehow in my google searching I found this advice: <So I suspect corrupted data files. delete /var/cache/apt/*.bin followed by “apt-get update” to reset apt.Which indeed fixed this error condition,> at [http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/](http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/).

I followed the instructions and removed the bin files in that directory from my computer, and all of a sudden apt-get and the package manager were working again!

Anyway, I have no idea why this worked, but I just wanted to post this somewhere in the ubuntu forums, since I couldn't find anything in the forums before when I was searching.
:)

---

### Post by okkie on 2007-08-30
**This post could be related to an Ubuntu bug filed at**: E: Type '‘deb' is not known on line 57 in source list /etc/apt/sources.list [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				thanks for your info.i have the same problem but could not fix it the way you did.
my computer says E: Type '‘deb' is not known on line 57 in source list /etc/apt/sources.list
did you perhaps come accross something similar?

---

### Post by wormser on 2007-08-30
> **okkie said:**
> **This post could be related to an Ubuntu bug filed at**: E: Type '‘deb' is not known on line 57 in source list /etc/apt/sources.list [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				thanks for your info.i have the same problem but could not fix it the way you did.
my computer says E: Type '‘deb' is not known on line 57 in source list /etc/apt/sources.list
did you perhaps come accross something similar?

Open up /etc/apt/sources.list and take a look at line 57 and post the results.  

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Hobo Joe on 2007-08-30
For installing things, don't use 'apt-get', and replace it with 'aptitude'.

This doesn't happen to it, and it hadles dependencies better.

---


---
title: "installation issues Can't install any apps"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by kerrymorgan1 on 2007-11-08
I tried to install a programme called Buddi 2.6.4.2 it went crazy and shut down ......... i have tried to restart it and reinstall it and it keeps on saying
Only one software management tool is allowed to run........... this was straight after a restart nothing else was going.
i have tried to run the synaptic installer to but i can't install anything there all because of buddi can anyone help?????

---

### Post by SpiritIsReality on 2007-11-08
howdy
To see if we can spot the software managers that are running, could you open a Terminal,
(Applications > Accessories > Terminal) and click the full screen box in the top right of
the Terminal.
At the command prompt, type
ps axu
and press enter.
Please copy and paste the results here. Unless you can find what you are looking for and give them the kill command.

If we're on the right track, then we're looking for /usr/bin/apt-get /usr/bin/aptitude and /usr/sbin/synaptic
the pid (process id) numbers are on the left hand side of the screen on the same line as the file names.
so if you spot /usr/sbin/synaptic in the list, like this for example
fred      6728  3.0  2.8  31556 10904 ?        S    02:26   0:00 gksu /usr/sbin/synaptic
root      6729 23.6  7.9  51940 30788 ?        Ss   02:26   0:06 /usr/sbin/synaptic
we could run 
kill -9 6728
kill -9 6729
and that would stop the synaptic package manager .
It sounds like /usr/bin/apt-get would maybe be on your list.
I think that a restart of your computer will fix the problem, by shutting down the package managers that are running.
That's probably the simplest thing to do. You could see if restarting your computer solves the problem.
Post back and let us know how you are doing.
trails

---

### Post by 1/0 on 2007-11-14
Try:

```

sudo dpkg --configure -a
sudo apt-get update

```

---

### Post by SpiritIsReality on 2007-11-14
> **1/0 said:**
> Try:

```

sudo dpkg --configure -a
sudo apt-get update

```

thanks

---


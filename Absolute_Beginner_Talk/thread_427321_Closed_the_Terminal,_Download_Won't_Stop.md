---
title: "Closed the Terminal, Download Won't Stop"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-04-29
As the title says, even if i closed the terminal, the download won't stop. Is there any way to make it do so?

---

### Post by Metacarpal on 2007-04-29
As long as you're still logged into a machine, a process you've started will continue until either it's done or you "kill" it.

If you're still in terminal and want to stop something that's running, pressing Ctrl-c will usually do it.  Otherwise:

From terminal, enter
```
pkill *processname*
```

For instance, if you're trying to kill a wget operation, do
```
pkill wget
```

That should stop it.

NOTE: don't pkill apt-get or aptitude.  It makes it cranky.

---

### Post by Happy_Man on 2007-04-29
All right, i'll remember that. And now we run into another issue. It finished downloading, but now it won't install. What gives? (FYI, i tried to put ubuntu-desktop on, then changed my mind halfway through.)

---

### Post by Metacarpal on 2007-04-29
What were you using to download ubuntu-desktop?  Synaptic, apt-get, aptitude, adept, other?  Are you doing this from a server (no-GUI) install, Kubuntu, Xubuntu, something else entirely?

When you say it finished downloading but won't install, was some sort of error message kicked to the screen?

Have you changed your mind back and want to go ahead and install ubuntu-desktop after all?  If so, re-running the aptitude (or apt-get) install ubuntu-desktop command should work.  Any packages that were already downloaded will be installed from your on-disk cache instead of being redownloaded.

Sorry for all the questions, just trying to make sure I'm giving answers relevant to your situation.

---

### Post by Happy_Man on 2007-04-29
Ah yes, that part about doing it over worked perfectly! (I feel stupid.) Thanks! :D

---

### Post by konungursvia on 2007-04-29
If the process is visible somewhere graphically, you can open another term and type "xkill" and then you'll see a skull cursor. Click on the window where the process is going, and it will be killed.

---


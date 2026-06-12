---
title: "Problems updating Add/Remove"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Jjjakal on 2007-08-26
Hi,
I just installed Ubuntu 7.04 last night, using Wubi.  Sofar, I love it.  Its got everything I use.

My only problem though, it with the Add/Remove tool.  When I run it, it says something along the lines of the list not being up to date, and if I want to reload the list.  I click reload, and the window greyes itself out like its working, and the mouse cursor changes to the working one, but then it just stays like that doing nothing.  I read another thread by a guy with the same problem, and he said he left it for a day and nothing happened, but there was no solution in that thread.  I have left mine for about 4 hours, will nothing happening.  When its "Updating" I cant close the window.

How can I get it to work?

---

### Post by rhylan on 2007-08-26
Hey, I'm only a new user myself here so this might be a case of the blind leading the blind...

Have you tried going to system>administration>update manager first? try that, and if that doesn't work try going to system>administration>synaptic package manager and searching for all available updates there

Sorry if you've tried this already, as I said I'm a beginner myself, so this may not be watertight advice, but I'm sure these two suggestions couldn't hurt you setup at least if you try them.

Good luck!

---

### Post by alienexplorers on 2007-08-26
Try typing in terminal:
> sudo apt-get update
sudo apt-get upgrade
You could also go into synaptic and hit reload

---

### Post by Jjjakal on 2007-08-26
Thanks.  I havent finished yet, but those are both going.  There were lots of updates, I didnt realize I needed to do that.  My guess is that it will solve my problem.  If it doesnt, I will post again later.

---

### Post by Jjjakal on 2007-08-26
Im back now, and cintinueing to try to fix this.  When I came back, the update manager was still running.  It seemed to be frozen, exactly as the add/remove tool was.  I restarted, and the number of updates went from 166 to 46.  

When I tried to run synaptic, it gave me an error. 

```
E:dpkg was inturrupted, you must manually run 'dpkg --configure -a' to correct this problem.
E:_cache->open() failed, please report.
```

When I try to run sudo apt-get update, I get the dpkg error a little ways into it.

---


---
title: "aMSN all weird - can't move window, no title bar"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Skyler0 on 2007-01-08
I restarted my computer, and now when I run aMSN it loads up and signs me in and everything, but there is no title bar or main menu (file/edit etc). I also can't move the window, and it appears on all my workspaces. I'm running BerylXGL if it has something to do with it, but idk what's going on.

Also if I double click the aMSN systryay icon I get an error

> can't iconify ".": override-redirect flag is set
    while executing
"wm iconify ."
    (procedure "iconify_proc" line 14)
    invoked from within
"iconify_proc"
    (command bound to event)


If I open a convo with someone, it works just fine. It's just the main window that is all messed up. idk what's going on :S

Thanks.

---

### Post by Skyler0 on 2007-01-09
nobody ever encountered this problem before :(.

---

### Post by alynx on 2007-06-07
i have the same problem :(

---

### Post by Najand on 2007-06-07
Stop Beryl and try to load amsn again. Check if it is an amsn problem or beryl's?

---

### Post by twistedtwig on 2007-06-08
I have the same issue with no beryl..

have dual monitors, not sure if they are 100% set up correctly.. need to play with those settings I think

---

### Post by sailor2001 on 2007-06-08
if you are running beryl, switch window manager to metacity

---

### Post by rvergarav on 2007-06-08
I have the same problem. I am using Beryl too.

---

### Post by Notter on 2007-07-25
I am having the same issue, as well. I am not using beryl.
I think it may be a setting withing aMSN itself.
Have no idea how to get back into the preferences to fix it.
:confused:

---

### Post by sudo panda on 2008-04-08
check if you have an amsn plugin called "winskin"
if so, unload it.
This should fix the problem. At least it did for me

EDIT: oops, forgot you couldn't access the title bar :) 
Run Terminal and enter: sudo amsn 
then when the amsn loads up you should be able to access Account > Select Plugins

---


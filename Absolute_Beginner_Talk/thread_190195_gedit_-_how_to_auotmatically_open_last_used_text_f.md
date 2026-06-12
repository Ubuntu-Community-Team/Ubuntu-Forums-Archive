---
title: "gedit - how to auotmatically open last used text files?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-06
Hi,

I need to work with several text files open at one time. When I close and reopen gedit, I want all my text files to be automatically reopened. At present I need to do this manually, which I want to avoid.

I have looked at other text editors but have found nothing that can do this.

My previous editor was EditPlus. Bluefish is very nice, but that also doesn't have an automatic open of last used files.

Is there anyway to make gedit or Bluefish do this? Alternatively is there a GUI text editor that does this?

Thanks.

---

### Post by aysiu on 2006-06-06
I believe Kate would be your text editor of choice, then, as it has sessions.

**Edit**: I just did a little testing... it's weird. If you select in the exit options to "Save session," the session doesn't really get saved. But if you select "Ask user," it does.

---

### Post by u.b.u.n.t.u on 2006-06-06
aysiu thanks for that. I installed the program with Synaptic but can't find it anywhere.

Any suggestions?

---

### Post by aysiu on 2006-06-06
Alt-F2 ```
killall gnome-panel
``` Otherwise, you can just right-click on the menu icon and select **Edit menu** and add it manually. The command to launch Kate is ```
kate
```

---

### Post by u.b.u.n.t.u on 2006-06-06
I have been testing a lot of text editors and I think I found one that automatically opens last used files - Screem. I don't know where the setting is, but I leave my files open, close the program and upon reopen, I see my files just how I left them.

[http://www.screem.org/](http://www.screem.org/)

I am still testing it but so far I managed to make it look and behave very similar to EditPlus (windows environment).

:grin: 

I really like how, little by little, ubuntu is doing everything I need it to do - only far better than my previous operating system.

---

### Post by David A Knight on 2006-06-06
There is no setting, screem saves its current state on exit, or when told to by the gnome session manager.

---


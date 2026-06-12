---
title: "3D Desktop"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-10-11
I want to get 3D Desktop running, at least on my main monitor, but when I tried to install what may or may not have been 3d desktop, I ruined my Ubuntu partition, and went mad trying to repair it.

Is there a beginner's walkthrough, including a section on figuring out whether or not my computer can handle it? Alternately, can someone help me with it?


Thanks in advance,
Brett

---

### Post by theknave on 2006-10-11
Okay, I've got it installed now (used Synaptic. How simple was that?) but it won't run. When I try to run it, this happens:

```
brett@Brett:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

brett@Brett:~$ 3ddeskd
Daemon started.  Run 3ddesk to activate.
brett@Brett:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

brett@Brett:~$



```

What's wrong?

---

### Post by redDEADresolve on 2006-10-11
[http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

---

### Post by theknave on 2006-10-11
> **redDEADresolve said:**
> [http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

See, last time I followed that tutorial, my computer wouldn't boot up in a GUI. I'd wrecked something, and my X wouldn't do what it was meant to.

---

### Post by theknave on 2006-10-11
Anyone, please? I'm sure it is a simple problem.

---

### Post by blitzer on 2006-10-11
I found this in the [URL="https://help.ubuntu.com/community/3ddesktopHowto"]Ubuntu WIKI 
[/URL]

:mrgreen:

---

### Post by podunk on 2006-10-11
You need to have 3d support on for your video card. Enter the command

```
glxinfo
```

and at the top of the gobbly gook you should see:
direct rendering: Yes

If that isn't there then you need to install the drivers for your video card.

---


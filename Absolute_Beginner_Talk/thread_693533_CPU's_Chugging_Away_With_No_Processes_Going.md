---
title: "CPU's Chugging Away With No Processes Going"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Patriot1776 on 2008-02-11
My dual core CPU is still chugging away when System Monitor shows all processes asleep, and in terminal sessions I have opened, the only thing that I really have going that should be causing all this is watching a live Web stream from VLC.  I wouldn't mind it for the fact that my CPU fan is loud when it's running constantly.  Any ideas?

EDIT - Nvm.  The feed had been lost and it was from the computer I think trying to reestablish the feed that it was happening.

---

### Post by Astinsan on 2008-02-11
You also have to remember that Linux (and windows 2000+) have file indexing services going in the background. It makes it easy to search for files or stuff in files. You can tweak the settings in the control panel applet. This is also on the system preference menu. 

Also you need to tweak the settings for the power daemon. Make sure its running by going into System > Administration > services  look for cpu frequency manager and make sure it is check and running. This service / daemon  throttles back the processor(s) when they are not in use or not needed. 

Linux hasn't been all that great in the power management department but it is getting better. My laptop used to burn up batteries really quick. Now I can get about 30 minutes more on a battery than with windows xp. 

Hope that helps.. 
Jay

---

### Post by Patriot1776 on 2008-02-11
Thanks much.  All that was enabled.  What happened is that the streaming video locked up and the CPUs went ape trying to resync it back up and/or restart it without restarting VLC.  Shutting down VLC solved the problem and I've since restarted VLC and got the video going again without problems.

CPU Frequency Manager makes the CPUs run at slower clock speeds when they are not being used?

---

### Post by Astinsan on 2008-02-18
If all is well it should scale the processor "on demand". 

There are a bunch of posts about the subject. Most regarding laptops. Desktops fit in this area too.  Most new world processors have the same power save functions. I don't know if the desktop graphics cards have the same options though.

---


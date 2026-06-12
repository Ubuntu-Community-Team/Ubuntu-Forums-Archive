---
title: "Startup Script??"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by se2schul on 2007-06-29
I need to execute some commands at startup. I'd like to put them in a script somewhere. Which script(s) can I add commands to that will get executed during startup?

Specifically, I want to add this command 'sudo modprobe ndiswrapper' to get my wireless adapter working automatically.

Thanks!

---

### Post by arvevans on 2007-06-29
Things that run at boot time are usually referred to in the various /etc/rc# files.    /etc/inittab is usually used for boot-time scripts which are pointed to by an /etc/rc#, where the # represents the proper run level for script execution.

You can also put calls to your scripts in your /home/[user_ID]/.profile and have them run whenever you log in.
_._

---

### Post by nick_h on 2007-06-29
You need to add ndiswrapper as an entry in /etc/modules - this file contains kernel modules that need to be loaded on boot.

---

### Post by se2schul on 2007-06-29
I added ndiswrapper to /etc/modules/ and it worked perfectly, thanks!
I also learned a little about what gets run when linux starts. Xubuntu Rocks! Thanks guys.

---

### Post by Rocket2DMn on 2007-06-29
Another good way to have scripts execute on computer boot (not login) are to call them from /etc/rc.local
Bootup scripts are typically stored in /etc/init.d/ in this case and must, of course, be executable.

---


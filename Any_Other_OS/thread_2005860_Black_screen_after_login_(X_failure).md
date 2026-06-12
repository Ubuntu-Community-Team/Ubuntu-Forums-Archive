---
title: "Black screen after login (X failure?)"
date: 2012-06-18
forum: Any Other OS
---

### Post by Agent_Riot on 2012-06-18
I think I know this answer, but i'd like someone to confirm it. I'm running Linux Mint 13 with Cinnamon(Formerly Natty Ubun) in the 64bit flavor. My issue though, is probably a Linux one in general. After installing Mint I updated my sources and then ran the command to reinstall all my programs from the text list of them. It worked fine. There was an error at one point where it said there were depndency errors, but i cleared those up. Once everything finished i shut down the machine. A few hours later I booted it up to do some work, and after logging in I get a black screen with the cursor. I tried changing the session at the login screen from "Xclient default" to "Gnome Desktop 2" just for kicks, and it worked. I got everything to display. However I really want the normal default Cinnamon desktop back.
 
I confirmed it's probably the window manager not loading. Why it loads for the other "session" choices is beyond me. A site I found told me to run this command..
 
dpkg-reconfigure xserver-xorg
 
Which is supposed to let me redo X. Is this right? Or is my problem more specific? I don't think it's a "Mint" specific issue. If it is I will head to their forums.
 
Thanks for the help!

---

### Post by Perfect Storm on 2012-06-18
Moved to Other OS/Distro Talk.

---

### Post by Dlambert on 2012-06-18
Install drivers maybe? And I've said this many time: I would not recommend Cinnamon ATM. But I would try to but into a Kernel/setting that works and maybe then install drivers.

---

### Post by Agent_Riot on 2012-06-18
Someone else mentioned that it could be drivers. Apparently there's a bug in Maya 13 that forces the Nvidia driver to load. I plan to go home and run some commands to try and restart Cinnamon/X. Here's to hoping they work. If it does I'll mark this thread as solved.

---

### Post by Birdman2010 on 2012-11-11
Has anyone found the solution to this problem?  The weird thing is that I can hit ctrl-alt-F8 and the Linux Mint 13 gui pops right open.  Any ideas and/or solutions?

---


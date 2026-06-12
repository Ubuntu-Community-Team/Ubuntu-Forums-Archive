---
title: "Failed to run /usr/sbln/synaptic as user root"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by johnmata on 2008-03-26
When I try to open the Synaptic Package Manager I get the following error: "Failed to run /usr/sbln/synaptic as user root.  Unable to copy the user's Xauthorization file"

Any help is highly appreciated.

Regards
,John

---

### Post by SunnyRabbiera on 2008-03-26
is this when you try to run synaptic in the menu's?
try a terminal and type in sudo synaptic

---

### Post by aysiu on 2008-03-26
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gksudo synaptic
``` If there are any error messages, paste them back here.

---

### Post by aysiu on 2008-03-26
> **SunnyRabbiera said:**
> 
try a terminal and type in sudo synaptic It really should be ```
gksudo synaptic
``` or ```
gksu synaptic
``` since it is a graphical application.

---

### Post by ddoxey on 2008-03-26
Using gksudo of gksu to invoke synaptic are awesome work-arounds.
But it seems that John's real problem is that he's lost the default behavior of selecting Synaptic on his Gnome menus.

John, if I were going to take a guess, I'd say this is related to some kind of corruption of your .Xauthority file. I've seen some other posts related to permissions on this file becoming corrupt during administrative activities.

I suggest you try this:
sudo chown john /home/john/.Xauthority

---

### Post by aysiu on 2008-03-26
They're not workarounds. They're actually how you launch Synaptic properly (unlike *sudo synaptic*).

And launching it in the terminal helps diagnose the problem, as it can give error messages back, whereas the Gnome menus cannot.

---

### Post by btlee on 2008-03-27
Is '/usr/sbln/synaptic' just typo?
The path is wrong.
Right path should be '/usr/sbin/synaptic'.

---

### Post by ddoxey on 2008-04-03
Well, I'm a CLI chauvinist as much as the next Linux guy.

But I wonder... what would be the proper procedure for diagnosing the malfunction with the Gnome menus?

John's problem is interesting to me because my menus are pretty goofy. I've tried copying the **xdg** directory from my laptop. That helped, but they just aren't just right.

Maybe there is a canned procedure for restoring the Gnome menus which would solve John's problem, as well as my own.

---

### Post by aysiu on 2008-04-03
The proper procedure is to launch ```
gksudo synaptic
``` from the terminal. The terminal will display error messages that will help diagnose the problem.

---

### Post by dea.dB.ear on 2008-05-01
I was trolling for answers to the same problem,  thought my laptop was over heating or something dire as lots of stuff was going haywire....

then i noticed I had a disk totally of trash....

worked fine with some disk space....

just thought i would mention it as a side effect of 0 bytes left...

ed

---

### Post by Argus on 2008-05-01
> **dea.dB.ear said:**
> I was trolling for answers to the same problem,  thought my laptop was over heating or something dire as lots of stuff was going haywire....

then i noticed I had a disk totally of trash....

worked fine with some disk space....

just thought i would mention it as a side effect of 0 bytes left...

ed

:guitar: That fixed it for me TKS

---


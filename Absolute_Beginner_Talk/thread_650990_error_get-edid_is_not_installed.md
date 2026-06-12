---
title: "error: get-edid is not installed"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by greeninoregon on 2007-12-27
I installed all of my updates today. I was prompted to restart. When I did, it started normally until it came to a screen that said this:
[INDENT]
*Starting anac(h)ronistic cron anacron  [ok]
*Starting deferred execution scheduler atd   [ok]
*Starting periodic command scheduler crond  [ok]
*Checking battery state  [ok]
*Running local boot scripts (/etc/rc.local)  [ok][/INDENT]


Where it freezes.


Then it finally goes to a screen that says:
 
[INDENT]"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
<Y/N>[/INDENT]

If you choose yes, it takes you to another screen:

[INDENT]/etc/gdm/failsafexserver: line 47: [: too many arguments 
Warning: Could not retrieve EDID because get-edid is not installed (1)
<OK>[/INDENT]

Which takes you to:
[INDENT]
The X server is now disabled. Restart GDM when it is configured correctly.
<OK>[/INDENT]

Then it goes back to:

[INDENT]
*Starting anac(h)ronistic cron anacron  [ok]
*Starting deferred execution scheduler atd   [ok]
*Starting periodic command scheduler crond  [ok]
*Checking battery state  [ok]
*Running local boot scripts (/etc/rc.local)  [ok][/INDENT]
(And doesn't do anything else... just sits there.)

I tried everything on this post: [http://ubuntuforums.org/archive/index.php/t-585420.html](http://ubuntuforums.org/archive/index.php/t-585420.html) and nothing worked. Going through the setup, and trying to install edid didn't work. Edid wouldn't install.


I tried to find an error report for this, but I couldn't. I read somewhere about customizing an edid file, but that's my last resort.

Any suggestions?

---

### Post by Mister.Vash on 2007-12-27
post the etc/gdm/failsafexserver file that you mentioned

Also, under the /var/log directory, you should hopefully have a Xorg.0.log file - if so post that as well

That may provide more details on what the system is trying to do, and maybe a better starting point

---

### Post by greeninoregon on 2007-12-27
> **Mister.Vash said:**
> post the etc/gdm/failsafexserver file that you mentioned

Also, under the /var/log directory, you should hopefully have a Xorg.0.log file - if so post that as well

That may provide more details on what the system is trying to do, and maybe a better starting point



It wouldn't let me access the xorg file from the safe mode, and I'm not quite sure how to access the other from the command prompt. Does it need a command before it?

---

### Post by querze on 2008-07-22
I got the same problem when I downloaded to the latest version of UBUNTO. They provide questions here but how do you get working answers. Thanks Richard

---


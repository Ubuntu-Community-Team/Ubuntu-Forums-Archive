---
title: "[SOLVED] Sessions &amp;quot;Startup Programs&amp;quot; tool broken in Intrepid?"
date: 2008-11-17
forum: Apple Hardware Users
---

### Post by hyperboloid on 2008-11-17
I added the command "/usr/bin/xmodmap ~/.xmodmap" to the Startup Programs in System -> Preferences -> Sessions, where ~/.xmodmap is a customization file for my keyboard.

The command was executed just once, on my next boot, and ever since it does not get run anymore. I can of course run it manually from the command line after logging in. 

Anyone else seeing such a problem?

---

### Post by stream303 on 2008-11-17
When I created a custom .xmodmap, I just created it in my home directory.  Then I logged out and back in, and Intrepid noticed the file, and threw up a dialog asking if I wanted to use that file, and also provided a checkbox to disable the dialog if you didn't want to see it anymore.

Maybe remove it from your startup programs, and just place that file in your home directory, and logout, or reboot, and see if that custom dialog box comes up.

At least this is what happened on my ppc iMac, although I think there shouldn't be any difference based on cpu architecture...

---

### Post by hyperboloid on 2008-11-18
> **stream303 said:**
> When I created a custom .xmodmap, I just created it in my home directory.  Then I logged out and back in, and Intrepid noticed the file, and threw up a dialog asking if I wanted to use that file, and also provided a checkbox to disable the dialog if you didn't want to see it anymore.

Maybe remove it from your startup programs, and just place that file in your home directory, and logout, or reboot, and see if that custom dialog box comes up.

At least this is what happened on my ppc iMac, although I think there shouldn't be any difference based on cpu architecture...

Yes, that works - thanks. :)

Just out of curiosity, I looked in the man page for xorg and  xorg.conf to see if I could figure out where the X server is being told to look for that file, but I couldn't find anything. Must be done somewhere else.

---


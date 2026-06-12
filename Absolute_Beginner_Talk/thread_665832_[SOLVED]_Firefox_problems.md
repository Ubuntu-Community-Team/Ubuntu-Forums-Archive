---
title: "[SOLVED] Firefox problems"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by patrickaupperle on 2008-01-12
I installed a plugin called tab something or another and used it for a while. I decided I did not like this plugin and got rid of it. Now when I have to force quit out firefox or my laptop comes unplugged and shuts off (my battery has gone bad and don't want to pay $130 for a new one) I do not get the "restore session" dialog. :confused::confused: I used to get this message and it is one of my favorite thing about firefox.

---

### Post by HereInOz on 2008-01-12
If no one else comes up with a better idea, you may have to uninstall firefox and then re-install it.  If you do uninstall, use the option in Synaptic to "Mark for Complete Removal".  Then reinstall and see how you go.  

You will lose all your settings and plugins, though, so perhaps hang about for a while to see if someone else does have a better idea.

---

### Post by patrickaupperle on 2008-01-12
Thankyou
I may try that in a while if there is not a better  idea

---

### Post by r4ik on 2008-01-12
Try the reinstalation option in synaptic nothing to lose.

---

### Post by patrickaupperle on 2008-01-12
I unistalled and reinstalled, but did not lose my plugins or settings :confused: 
I have not had a chance to test a force quit

---

### Post by HereInOz on 2008-01-12
Your plugins were saved in the .mozilla folder in your home directory.  If you still have difficulties, uninstall, delete the .mozilla folder from your home directory, then re-install firefox.

You will need to view hidden files and folders in Nautilus to be able to see the .mozilla folder.

---

### Post by HereInOz on 2008-01-12
And if you really, really have trouble, you may need to delete the /usr/lib/firefox directory as well, if it is still in existence.

---

### Post by patrickaupperle on 2008-01-12
Is there anyway to test if the restore session thing is working?

---

### Post by Tenken on 2008-01-12
If you log out while Firefox is open, next time you try to open it it will bring up the restore session message.

---

### Post by patrickaupperle on 2008-01-12
The first time i logged out with firefox running, when I logged back in it said "firefox is already running but is unresponsive. If you want to run this application, you must quit the program or restart" or something like that. After a restart no asking about restore session. After that I tried again (logging out) and it just opened normally. No Dialog :confused::confused::confused:

---

### Post by Moop on 2008-01-12
In firefox type```
 about:config
``` into the address box and click enter. In the filter box type sessions or sessionstore.

browser.sessionstore.enabled (bool) - Activate the service. Default is true. 
browser.sessionstore.resume_from_crash (bool) - Resume sessions post-crash. Default is true. 
browser.sessionstore.resume_session_once (bool) - Resume session at the next application start, but not again. Default is false.

Check those values and change them if need be. You probably will need to log out of Firefox for the changes to take effect.

---

### Post by Tenken on 2008-01-12
Type this in the terminal then try opening Firefox
```
killall firefox-bin
```

---

### Post by HereInOz on 2008-01-12
I think Moop has got it.  I knew there was a better way :-)

---

### Post by patrickaupperle on 2008-01-12
Thank you all for the wonderful help:KS
Moop Figured it out:KS:KS

:guitar:

Ubuntu forums are the best part of my linux experience.
Always so helpful, I think these forums are the reason I don't go back to windows.:KS

---


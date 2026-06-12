---
title: "Feisty - Restore Quit Options?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-07-11
I've lost the choices from the ubuntu panel's 'quit' icon. I used to have the standard options: quit, suspend, reboot, etc but now clicking immediately reboots to the logon screen. 

I've searched gconf editor for 'reboot' 'suspend' 'quit' etc  and made sure gdm.conf SystemMenu is enabled per some other threads, but I can't get the options back. I am running the standard feisty setup - no magic desktops, themes, etc.

I have used terminal commands for reboot, poweroff, etc for several weeks but would really like to be able to click the quit icon in the panel. Is there a way to restore these options other than reinstalling ubuntu?

Thanks for replies.

---

### Post by kyphi on 2007-07-16
Can you get the exit functions back if you delete the exit icon in the top right of the panel and then right click on the top panel and then use Add to Panel?  Don't forget to unlock the item first.

I had a look in the configuration editor under apps and then panels but could not find individual entries for the usual list of options.  That does not mean that it isn't there.

If you go to System - Admin - Login Window - Security and take the tick out of Enable Automatic Login, you should have a selection of Logout options in the bottom left corner.

Hopefully something will work.  Would you let me know, please?

---

### Post by drs305 on 2007-07-21
kyphi,

Thank you for your response.

Deleting and adding the quit icon didn't help.

I tried disabling autologon but still didn't have any logoff options in the security tab. 

My laptop had a program called gtweakui on it and I installed gtweak/gtweakui from the synaptic menu. That added/restored the logout options to the quit icon.

---


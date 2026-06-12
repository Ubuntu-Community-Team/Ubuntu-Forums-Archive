---
title: "onboard not appearing in Notification area"
date: 2006-10-18
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-18
Hello, 

I hope that I am understanding it correctly: 

I suppose that checking 'show icon in system tray' in the settings of onboard should make onboard appear in the notification area where also gaim appears when it is launched? 

In fact, when I check that setting, onboard does disappear from the bottom panel, but it does not appear in the notification area. This happens both with vnc and with nx. 

Or is the system tray not the notification area of ubuntu? (Sorry, but I am not very used to the terms used in ubuntu/gnome/linux yet.) 

frafu

---

### Post by t0rtois3 on 2006-10-19
This feature is only available on edgy at the moment as it needs the new version of GTK.

---

### Post by frafu on 2006-10-19
I am running edgy; I upgraded a few days ago.

---

### Post by t0rtois3 on 2006-10-19
Your right, it's not working here either

---

### Post by t0rtois3 on 2006-10-21
It was looking in the wrong place for the icon.  I'm to late to get the fix into edgy now though.

---

### Post by frafu on 2006-10-21
Good job! 
:-)

If I get you correctly, it is to late for the edgy-cd!? 

Will the fix be available through the Update Manager? Or maybe new debians to download from a webpage? 

frafu

---

### Post by t0rtois3 on 2006-10-22
Not sure i'll have to ask about the policy. You can bodge the fix yourself:

Press alt-f2 and type gksu gedit
Open the file /usr/share/onboard/sok.py and go to line 83.
Change the line from  
self.statusIcon = gtk.status_icon_new_from_file("onboard.svg")

to 

self.statusIcon = gtk.status_icon_new_from_file("%s/onboard.svg" % self.SOK_INSTALL_DIR)

Be carefull not to change the indentation.

Chris

---

### Post by frafu on 2006-10-22
Hello,

Thanks for the fix; I can confirm that the fix works. 
:-) 

Another problem has arised: when I click on the icon of onboard in the notification area, onboard disappears.  However, when I click again on the icon, it reappears, but it does not reappear on the same place on the desktop as it was before disappearing. 

The behaviour is different when using the taskbar: it reappears where it was before. 

I suppose that it should reappear where it was, also when using the notification icon; or am I wrong? 

frafu

---


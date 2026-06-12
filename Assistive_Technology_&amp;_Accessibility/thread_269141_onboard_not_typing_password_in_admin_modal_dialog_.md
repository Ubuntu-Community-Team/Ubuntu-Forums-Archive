---
title: "onboard not typing password in admin modal dialog box (dapper)"
date: 2006-10-01
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-01
Hello,

I would like to know whether anybody is able to type with onboard in the modal dialogbox asking for the admin password (for example when opening the Update Manager)?

As a modal dialog box usually blocks access to any other application until the dialog box has been dismissed, it is logical that onboard is not accessible during that time. 

Because of this issue, a m2-user will not be able to do administrative tasks using the gui. Consequently, I hope that the developers are looking for a fix before the release in edgy (if a fix is not already available). (I am currently trying onboard on dapper, forwarding the session through vnc to macosx.) 

Sorry if I am sounding a bit pretentious; but it would be great if onboard was working in as most situations as possible. 

frafu

---

### Post by Henrik on 2006-10-01
It is possible to change this in both dapper and edgy, but you have to change a gconf key. 

To do that you must first enable the menu choice for the gnome configuration editor. In that search for gksu and tick the disable-grab box.

We have a patch for Edgy that should let you do this with a check box from System -> Preferences -> AT-prefs 

I agree that the on-screen keyboard should work everywhere. KDE and the login screen are our next targets.

---

### Post by frafu on 2006-10-02
> **Henrik said:**
> To do that you must first enable the menu choice for the gnome configuration editor. In that search for gksu and tick the disable-grab box.

We have a patch for Edgy that should let you do this with a check box from System -> Preferences -> AT-prefs 


Thanks for the solution. It does indeed work; at first glance, it seems that the modal dialog becomes modless. 

Isn't it possible for the onboard-debian-package to activate the 'disable-grab' checkbox during the installation? Or maybe even better: have onboard check that setting on launch and activate it automatically if it isnt activated? 

Further, could you please tell me whether the solution works for any modal dialogue or only in applications that are at-spi aware? 

> 
... the login screen are our next targets.

That sounds very good. 
8)

---


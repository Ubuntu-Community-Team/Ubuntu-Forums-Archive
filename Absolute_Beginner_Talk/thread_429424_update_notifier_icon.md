---
title: "update notifier icon"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by aabento on 2007-05-01
Hello

Since version 6.10 _I do not have update to notifier icon_ in the superior panel. Now with update for version 7.04 this problem continues :( . I have updates to load but icon never appears me. How to make that icon reappears?:confused: 
Thanks

Arnaldo

---

### Post by starcraft.man on 2007-05-01
Run this command in terminal:

```
sudo aptitude search update
```

at the bottom do you see...?

```
update-manager
update-manager-core
update-notifier
```

They should all say i to the left. If your missing any of them install em via the terminal.

If they are all installed, I'm not sure where the preferences for them are. Might be corrupt, maybe removing em and putting em back via repos would make it work again?

---

### Post by chewearn on 2007-05-01
Forgive me, if what I'm about to suggest is wrong (since its so obvious). ;-)

Maybe its just a case of missing "Notification Area" applet?  

Right-click on the panel > Add to Panel; scroll to the bottom and find "Notification Area"

---

### Post by aabento on 2007-05-01
[HTML]Forgive me, if what I'm about to suggest is wrong (since its so obvious).

Maybe its just a case of missing "Notification Area" applet?

Right-click on the panel > Add to Panel; scroll to the bottom and find "Notification Area"[/HTML]


Perhaps so simple as you say Astalavista :)  :confused:  . I do not know why it disappeared. Now I added two areas of notification  :)   :)  . I will be waiting for new updates and we will see.
Thanks for yours help.

Arnaldo

---

### Post by Liakath on 2007-06-14
> **aabento said:**
> [HTML]Forgive me, if what I'm about to suggest is wrong (since its so obvious).

Maybe its just a case of missing "Notification Area" applet?

Right-click on the panel > Add to Panel; scroll to the bottom and find "Notification Area"[/HTML]


Perhaps so simple as you say Astalavista :)  :confused:  . I do not know why it disappeared. Now I added two areas of notification  :)   :)  . I will be waiting for new updates and we will see.
Thanks for yours help.

Arnaldo

I also have the same problem. I have all the packages installed. As well I have the notification area applet running. Still I miss the cute;) orange update notifier icon. I tried running update notifier both as normal user and sudo. I get the following errors. 
[COLOR="Red"]
liakath@HomePC1:~$ update-notifier
** (update-notifier:6186): WARNING **: already running?
liakath@HomePC1:~$ sudo update-notifier
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** (update-notifier:6198): WARNING **: not starting because user is not in admin group
liakath@HomePC1:~$ [/COLOR]

Rather strange responses!!. Any clues please.

I reinstalled all the three packages.
[COLOR="Red"]update-manager
update-manager-core
update-notifier[/COLOR]

But still no go

---


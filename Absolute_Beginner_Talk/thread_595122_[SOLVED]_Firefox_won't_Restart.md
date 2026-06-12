---
title: "[SOLVED] Firefox won't Restart"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-10-28
When I try to restart FF, for any reason, it shuts down and I just stare at my desktop. After a while if I click on the FF button to start it up I get a notification stating that FF is already running and to shut it down or reboot.

 I'm tired of rebooting just to close FF so I'm asking for a terminal code to quit the browser. Or maybe the solution to the doesn't close problem.

Many thanks,

Jon

---

### Post by Crafty Kisses on 2007-10-28
> **Romin-1 said:**
> When I try to restart FF, for any reason, it shuts down and I just stare at my desktop. After a while if I click on the FF button to start it up I get a notification stating that FF is already running and to shut it down or reboot.

 I'm tired of rebooting just to close FF so I'm asking for a terminal code to quit the browser. Or maybe the solution to the doesn't close problem.

Many thanks,

Jon
You need to go into System Monitor, and close one of the two Mozilla applications that are running, this happens to me all the time. :KS

---

### Post by Romin-1 on 2007-10-28
Thanks Codename, tis a lot better than rebooting.

Was going to go into profile and delete the Localstore to see if that would help but was a little reticent as that will mess up some of my settings.

Jon

---

### Post by haldean on 2007-10-28
also, you can just go to a terminal (or hit Alt+F2) and type 
```
killall firefox-bin firefox
```

---

### Post by Crafty Kisses on 2007-10-28
> **Romin-1 said:**
> Thanks Codename, tis a lot better than rebooting.

Was going to go into profile and delete the Localstore to see if that would help but was a little reticent as that will mess up some of my settings.

Jon

No problem man. :)

---

### Post by Romin-1 on 2007-10-28
Thanks for the code haldean,

Found an extension, Accessibar, that was causing FF to not restart. At least in my case that was the culprit...

Jon

---


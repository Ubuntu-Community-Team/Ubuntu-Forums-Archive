---
title: "Xfee desktop problem..."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by ionizd on 2007-12-13
Hi!
 I'm using Xbuntu (newest version) on an HP Pavilion N5150 laptop and everything was working swimmingly until I allowed the latest software update. When I restarted my laptop, the panels at the top and bottom of the desktop weren't there. It's kind of difficult to find my applications without them.
      Thank you!

---

### Post by santiagoward2000 on 2007-12-13
> **ionizd said:**
> Hi!
 I'm using Xbuntu (newest version) on an HP Pavilion N5150 laptop and everything was working swimmingly until I allowed the latest software update. When I restarted my laptop, the panels at the top and bottom of the desktop weren't there. It's kind of difficult to find my applications without them.
      Thank you!

Hi!
Try pressing Alt+F2 and type:
```
xfce4-panel
```
and see if this puts them back there.

---

### Post by innuendosoft on 2007-12-13
Looks like applet crash issue. Have you checked it's not related to the screen resolution. you can try adding the panels manually by going to the Administrative menu (if you are able to do that somehow).
Regarding the update, did you get any errors?

---

### Post by ionizd on 2007-12-13
That worked. Now, how do I ensure that it runs properly at startup?

***EDIT***
 I got it working properly now. What I had to do is run the panel applet manually as suggested by Santiagoward2000, then enable the "Show desktop menu on right-click" in Applications>Desktop Settings>"Behavior" tab. Once that was done, I then right-clicked the desktop and selected "Quit" to bring up the system logout, shutdown and restart selections (The Quit button on the panel forces one to exit the panel applet, which shuts down the panels). I then restarted the laptop, saving the session. Problem solved!

---


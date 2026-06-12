---
title: "removing azureus from startup"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by zanjabeel5 on 2008-03-27
Hi 
months a ago I wanted azureus to start-up with my system. I remember I tried a couple of things things
1- using sessions I added it to startup programs
2- ran azureus and used "remember currently running application"

no I don't want azureus to startup anymore, so I removed it from sessions -> "startup programs"
but it still starts up with the system.

any ideas.

---

### Post by codeslicer on 2008-03-27
So you went into sessions, removed it from the start up list, removed it from the current running apps list, and clicked remember currently running applications when it isn't running?

---

### Post by TeoBigusGeekus on 2008-03-27
Go to 
/home/yourusername/.config/autostart

Is Azureus listed there?

---

### Post by zanjabeel5 on 2008-03-28
I just removed it from startup programs and current session but didn't click "remember"
becasuse I wanted normal session  ... 
I'll give it a try. sounds logical.



Thanks for your help both,

Edit:
**[COLOR="Green"]it worked. should have chosen remember. Thank you both again[/COLOR]**

TeoBigusGeekus : it's not listed . but the following where listed 
bluetooth-applet.desktop  evolution-alarm-notify.desktop  trackerd.desktop

I don't need all that should I simply delete those file ?

---

### Post by TeoBigusGeekus on 2008-03-28
First delete them from session manager and if that doesn't work then delete the files themselves.

---


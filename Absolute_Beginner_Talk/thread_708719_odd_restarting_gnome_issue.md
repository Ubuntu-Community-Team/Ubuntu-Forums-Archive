---
title: "odd restarting gnome issue"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-02-26
I went to dinner and was gone maybe 45 minutes and upon my return, my desktop as i had left it (nothing running) was a white wavy screen and I could not get back to my desktop so im assuming my xerver quit so I did a Ctrl Alt Backspace and relogged in and everything was fine..

But why would it choose to do this now?  Ive had it in the nothing running state and nothing occured and I was able to move the mouse and the desktop came back to normal..I shouldnt be  concerned, should I?

---

### Post by Crafty Kisses on 2008-02-26
> **sox fan Matt said:**
> I went to dinner and was gone maybe 45 minutes and upon my return, my desktop as i had left it (nothing running) was a white wavy screen and I could not get back to my desktop so im assuming my xerver quit so I did a Ctrl Alt Backspace and relogged in and everything was fine..

But why would it choose to do this now?  Ive had it in the nothing running state and nothing occured and I was able to move the mouse and the desktop came back to normal..I shouldnt be  concerned, should I?

Probably not, if you really wanna look what happened you can always look at your .xorg log files.

```
nano /var/log/Xorg.0.log
```
Hope this helps, don't worry, you should be OK. :)

---


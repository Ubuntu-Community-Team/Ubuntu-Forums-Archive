---
title: "xfce4 panels fail to load"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by mr.v. on 2006-12-08
Hi all--

I just switched to XFCE4 from Gnome (thanks Taurus) since Gnome was really slow on my old computer. XFCE4 is much faster, and I was playing around with the configuration.

I made the panel stick to the bottom and enabled a few features, added a menu, and monkied around with the themes a bit (and ended up on clearlooks).

Anyway, I placed a terminal icon as a program launcher and everything was working great. Then all of a sudden, when I pressed the terminal icon, it would no longer launch a terminal. I thought this was weird. Other parts of the panel still seemed to work (like the clock kept ticking) and the menu button popped up a menu.

Anyway, I logged out and logged in again to see if that would fix the terminal button, but instead the panel no longer shows up (I had it at the bottom). It disappeared. Vanished...So I did some searches and found that I should go to the Panel section in SEttings manager. So I right click on the desktop, click settings | setting manager and there's a button called "Panel" I push it and nothing happens. All the other buttons like mouse, display, etc all pop open a settings config, but "panel" doesn't. I think it may be broken. I rebooted again, but it still doesn't load. I don't get any error message or anything...it just doesn't load.

How can i figure out what happened? Why is the panel section broken?
I really like XFCE because it's fast enough on my computer to make ubuntu run tolerably. I really don't want to switch back, but the missing panel is a problem.

Thanks for the help!

---

### Post by taurus on 2006-12-08
Can you open a terminal from the menu in the upper left corner?  If you can, open it and try to run this command at the prompt!

```
xfce4-panel &
```

---

### Post by mr.v. on 2006-12-09
So it worked! my panel came back as it had been configured with everything in its place that I had set it. It disappeared again when I closed the terminal window, which made me a bit worried. But then get this, now when I restart...it's there again!

So somehow that fixed it because I had rebooted several times before it and it wouldn't load. The only thing I changed was run the xfce4-panel as you said.

Should I be worried? Is there something gravely wrong with my init or config files that may have caused this bizarre issue?

Thanks again, Taurus!

---

### Post by taurus on 2006-12-09
If your panel comes back after a few logouts and logins, I wouldn't worry about it.  Everything is back to normal in the land of XFce4 now...  ;)

---

### Post by tvtalkshowshigh on 2006-12-14
i had the same problem, with my panel just vanishing when i  switched on thismorning. xfce4-panel fixed it, but i've no idea what caused it happen in the first place...

---


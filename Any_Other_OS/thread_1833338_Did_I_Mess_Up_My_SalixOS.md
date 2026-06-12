---
title: "Did I Mess Up My SalixOS?"
date: 2011-08-25
forum: Any Other OS
---

### Post by XubuRoxMySox on 2011-08-25
[Got the urge to try a new distro]("http://robinsrantsandraves.wordpress.com/2011/08/19/a-xubuntu-fanboi-looks-at-salix-os/") right before school started. Dumb when you have only one 'puter and you need it for school, but my "inner geek" would not rest until I tried SalixOS.

I downloaded the LXDE version (I wanted to have a look at LXDE again - it's been a year now) and it absolutely flew at superb speed on the LiveCD. Fastest Live experience ever! Everything worked, so I installed it next to my Xubuntu 10.04.

Didn't care for LXDE on Salix, though, so I installed Xfce and removed a bunch of the LXDE stuff (except that superb file manager). When I did that, Salix suddenly went to a crawl and balks when I open more than *one* application at a time! Very strange, especially after that awesome LiveCD experience.

I'm wondering if I messed something up by replacing the LXDE desktop with Xfce. And the forums there are nice and people are helpful, but the only answer they can give to my question is, "that doesn't make sense."

LOL, maybe I'm just not explaining it very well. But I wonder if my experience was unique. If so, then I have to believe I messed it up somehow. I'll wait for the Xfce LiveCD to be released before trying again.

-Robin

---

### Post by IWantFroyo on 2011-08-25
Maybe Salix used some LXDE or LXDE-dependent program(s) to keep it running that quickly.
What happens when you open an app from the command line? Do you get a whole bunch of error messages?

---

### Post by XubuRoxMySox on 2011-08-25
> **IWantFroyo said:**
> Maybe Salix used some LXDE or LXDE-dependent program(s) to keep it running that quickly.
What happens when you open an app from the command line? Do you get a whole bunch of error messages?

Some of them work, but most don't. I had the browser open and wanted to copy-and-paste some upgrade stuff to the terminal, but when I opened the terminal it locked up and refused to function until I closed the browser! One application at a time. Very weird.

No biggie. I may have messed it up trying to upgrade from 13.1 to 13.37 too while it was behaving like that. I guess I thought an upgrade might fix it. No luck... I don't think it even upgraded successfully anyway. 

I'm pretty sure I messed it up, just trying to see what I can learn from the experience. I don't think there was any LXDE-dependent stuff that I removed to cripple the OS like that, but it's possible. Even likely, lol.

---

### Post by 4Orbs on 2011-08-25
When you removed lxde, did you also remove the lxde session mgr? If you didn't, then it may be spawning a second instance of xscreensaver daemon. Happens to me when switching back and forth between different desktop sessions.

---

### Post by XubuRoxMySox on 2011-08-25
> **4Orbs said:**
> When you removed lxde, did you also remove the lxde session mgr? If you didn't, then it may be spawning a second instance of xscreensaver daemon. Happens to me when switching back and forth between different desktop sessions.

Now THAT makes sense! That's it. SOLVED, lol. Thanks!

---


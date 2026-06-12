---
title: "Fized freqeuncy monitor with Live CD?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by deafcon on 2006-03-26
I want to mess around with the live CD, but I'm having some trouble getting the right resolution.  My monitor is from an old Sun workstation and it will only use a very narrow range of resolutions.  In windows I use 1600x1200@60hz, is there any way to force the Live CD to use those settings?  If not with the Live CD, is there a way to do it with a full install?

---

### Post by oscar on 2006-03-26
If your graphics card is properly detected and it is only the x config that is not correct then I think I have a solution, it works on my laptop getting kororaa (another live cd) to use my laptops 1280x800 resolution.
Edit your /etc/X11/xorg.conf
at the bottom of the file there should be a screen section in there. For me there is a line:
```
    DefaultDepth    24
```
So I edit the display subsection corresponding to that depth and add the resolution at the beginning of the Modes section. I deleted all the other modes because I dont want them but you can leave them there.
```
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
```
 After that log out and when you get to the gdm press Ctrl+Alt+Backspace to restart the x-server, log in again and you should be able to select the right resolution. System > Preferences > Screen Resolution

---


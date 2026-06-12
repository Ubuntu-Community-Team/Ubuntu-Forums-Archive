---
title: "Screensaver / Desk Lock run in wrong, smaller resolution"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-04-25
I thought I had all of my resolution woes behind me. I got Xserver to run 1600x1200 when docked and hooked up to my Dell 21 Flat Panel. I found a script that will detect my docked or undocked status and load one of two customized xorg.conf 's

However... I go to lock my workstation today and notice that the password prompt and screensaver beneath it are running at 1024x768 in a box at the top left of my screen (with the rest of my desktop at the correct resolution and clearly visible beneath it.)  That won't do....

Anyone have an idea how to fix this?

---

### Post by mybootorg on 2006-05-02
I ****FINALLY**** found a solution to this.   The other day on a whim I installed the Gnome Screensavers package. Its pretty basic.  Not too many choices - like 3 or 4 choices of screensavers and none of them very interesting. But guess what. They run at the correct resolution and desklock works fine too.

This led me to investigate the problem from a strictly XScreensaver angle and the solution I found made me laugh.... it made me a laugh a big pirate laugh at the pure ridiculousness of it.  **[COLOR="Red"]HAR HARRRR HAR-HAR HARRRR HARRR![/COLOR]**

Here's what I found. From the Xscreensaver faq:

[QUOTE=Xscreensaver FAQ]This is a bug in the X server, not xscreensaver: the XF86VidModeGetViewPort() function is full of lies, and I don't see any way to work around it.

I believe this only happens on certain laptops, and possibly only on systems that have a docking station or external monitor that runs in a different resolution than the laptop's screen.[/quote]

Sound familiar?  Why yes it does...

[QUOTE=Xscreensaver FAQ]
There is discussion of this bug in the Red Hat and Debian bug systems; the buck was finally passed upstream to XFree86, where it is bug 421.

The XFree86 developers have closed the bug. As far as I can tell, their reason for this was, "this is an X server bug, but it's pretty hard to fix. Therefore, we are closing it."

So how about that. If you'd like them to actually fix this, you'll have to convince them that it matters, I guess...

In the meantime, you can work around this by editing your .xscreensaver file and setting the "GetViewPortIsFullOfLies" preference to True. That will make xscreensaver always run on the full size of the desktop, regardless of what lies the server tells about the currently-visible area. (This preference was added in version 4.16, May 2004.) [/QUOTE]

**[COLOR="Red"]HAR-HAR HARR![/COLOR]**

---


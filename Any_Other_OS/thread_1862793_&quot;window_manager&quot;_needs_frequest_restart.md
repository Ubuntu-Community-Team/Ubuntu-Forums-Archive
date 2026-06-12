---
title: "&quot;window manager&quot; needs frequest restart"
date: 2011-10-12
forum: Any Other OS
---

### Post by SaintDanBert on 2011-10-12
NOTE -- I've installed Linux Mint-11 and selected the "Ubuntu" prefix.
I hope I did the right thing.  Yes, I know I can post to the Mint-specific blogs, but this feels like it belong here more than there.
-------------------------------------
For some reason that I have yet to discover, much less resolve, I must restart the "window manager" on my Mint-11 laptop. I believe that I have Compiz off and only Metacity running. When things go wrong, the four-panel desktop switcher stops working and all windows lose their title bar and border. They also get jammed against the bottom edge of the top panel. They may also be up under the top panel.

I can use the "Compiz Icon" applet and "restart window manager" to get things back to reasonable for a while.  After a while, it happens again and the process repeats.

I've looked in logs and do not find evidence that I would equate to "crash" or similar. However, I have no idea what I should be looking for. I'll gladly post whatever folks think are helpful as diagnostic information or conduct experiments seeking diagnostic information.
Other than, "... I have a problem with my window manager ..." I don't even know enough to know what else I need to report.

My hardware is Intel Graphics GL965/GM960 video in a thinkpad laptop.

File **/var/log/xorg.0.log** does not contain any error (EE) records.

Thanks in advance,
~~~ 0;-Dan

---

### Post by CharlesA on 2011-10-17
Perhaps the video driver had some sort of problem and caused something else to crash? I haven't used Mint at all, so that's just a shot in the dark.

---

### Post by SaintDanBert on 2011-10-20
I don't find any "error messages" in any of the logs to tell me what is going on.

There must be some way to get some visibility on what is happening.

Very Frustrated,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-11-01
I continue to require [Compiz Icon] --> [Restart Window Manager] on my laptop.  I have no idea why this is going on.  I don't find any log entries or error messages that offer a clue where to look further.
[highlight] Can anyone out there offer any real help or guidance? [/highlight]

Perhaps I need to remove (purge?) and re-install metacity and similar parts to get it running again.  With all of the Unity and Compiz and Xorg and other parts I have no clue how to do this without completely killing my graphical desktop.  [I confess that I likely tinkered myself into the mess I have, but I have no idea what I did that broke whatever is broken.]

Please help,
~~~ 0;-Dan

---

### Post by CharlesA on 2011-11-01
Could try purging it and reloading. Not sure if that will break anything tho.

---

### Post by SaintDanBert on 2011-11-02
> **CharlesA said:**
> Could try purging it and reloading. Not sure if that will break anything tho.

I agree, but what is **"it"**?
Consider a possible synaptic session: (or command line equivalent)
[list]
[*]open synaptic
[*]enter "metacity" into the search dialog
[*](my box currently reports 72 matching packages with various names)
[*]select packages to "purge" -- **which packages?**
[*]... does it make sense to restart the X11 server here ...
[*]select packages to re-install
[*]... does it make sense to restart the X11 server here ...
[/list]

Cheers,
~~~ 0;-Dan

---


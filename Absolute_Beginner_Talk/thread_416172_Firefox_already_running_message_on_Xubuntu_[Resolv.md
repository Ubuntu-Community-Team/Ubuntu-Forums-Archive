---
title: "Firefox already running message on Xubuntu [Resolved]"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-04-20
When I try to open Firefox on Xubuntu I often get a message titled "Close Firefox"  Text of the message is: Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process or restart your system.

I can't find any Firefox process running in order to close it.  What's going on?  Thanks.

---

### Post by Ziox on 2007-04-20
> **sagesparrow said:**
> When I try to open Firefox on Xubuntu I often get a message titled "Close Firefox"  Text of the message is: Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process or restart your system.

I can't find any Firefox process running in order to close it.  What's going on?  Thanks.


Most likely, the previous Firefox process hasn't been unloaded yet, and the two process are running into some conflict.  You can open up the process manager and look for a process called firefox-bin.  Shut down that (or them), and then start firefox again.

---

### Post by sagesparrow on 2007-04-20
Thanks.  I've looked there.  Sometimes it's there and I can kill it, but most of the time it's not in the process manager.  Any other ideas other than restarting?  Is there some reason why firefox is not closing completely?

---

### Post by diatribe on 2007-04-20
no idea why it would say that, but a killall firefox-bin should do the trick if it happens

---

### Post by Ziox on 2007-04-20
> **sagesparrow said:**
> Thanks.  I've looked there.  Sometimes it's there and I can kill it, but most of the time it's not in the process manager.  Any other ideas other than restarting?  Is there some reason why firefox is not closing completely?

Does firefox start up if you've complete killed the process?  Sometimes, I click my icon, and nothing happens, and more clicking doesn't do anything either.  So I had to go to process manager and kill firefox-bin (sometimes there are multiple instances).

I personally have no idea why firefox isn't closing completely (if that's the problem at all)

---

### Post by sagesparrow on 2007-04-20
If the foxfire-bin is listed in the process manager and i kill it, then i can start a new foxfire up.

---

### Post by diatribe on 2007-04-20
yes thats because firefox doesnt allow two instances of itself to run; you have to kill any previous firefox-bin processes before running it again

---

### Post by sagesparrow on 2007-04-20
If I single click on Firefox icon then the cursor looks like it's opening the browser, but nothing happens.  Then if I double click it, I get the already running message.  But I get that message even if I just double click Firefox without the initial single click.  This situation covers all different attempts at opening FF in different ways.  What gives?

---

### Post by Ziox on 2007-04-20
It's interesting to note that I only get that problem in Xubuntu...perhaps it is how XFCE draws firefox. 

you can see the outputs by starting FF from Terminal.

---

### Post by diatribe on 2007-04-20
when you do get firefox running, how do you terminate it?  do you click the close button, go to file->close, or what?  because the process shouldnt be staying open.  also, when you do get it running, how do you open it?  by a link on the desktop, from terminal, etc?

---

### Post by aysiu on 2007-04-20
Try this:
[http://kb.mozillazine.org/Profile_in_use#How_to_unlock_your_profile](http://kb.mozillazine.org/Profile_in_use#How_to_unlock_your_profile)

---

### Post by sagesparrow on 2007-04-20
I close it with the close button in the upper right corner.  I open it (or try to) using the icon in the panel or trying Applications, Network, Firefox.  I can't really see a pattern for the times that it opens as opposed to when it won't.  Maybe it's my imagination, just it seems to be getting less frequent that it opens.

---

### Post by sagesparrow on 2007-04-20
Thanks.  How do I find the Profile folder, etc. as recommeneded in that article?

---

### Post by Ziox on 2007-04-20
open nautilus or thunar and hit ctrl+h, then look for either .mozilla folder or .mozilla-firefox folder and look for the file/folder...

---

### Post by sagesparrow on 2007-04-21
Thanks.  I'm starting to think that maybe it has something to do with closing Firefox when there are multiple tabs open.  I'm using an older machine with only 128 Ram.  Perhaps going to an older version of FF (not FF2 that I'm running) and closing tabs one by one before closing firefox might help.  Does that seem a useful direction to pursue?   I'll experiment around with that.

---

### Post by sagesparrow on 2007-04-21
Here's what I found out:
I created another user and found that Firefox worked fine for the new user.  I suspected that one of the extensions I had added was the culprit.  When, by chance, I finally got Firefox opened in the root user I checked out the addons and noticed Foxmarks Bookmark Synchronizer.  No other extension I had added would be potentially operating on the web underneath the processes.  I uninstalled that and PROBLEM SOLVED!

Thanks for your help.  So add this to the knowledge banks.

---


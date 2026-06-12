---
title: "Firefox keeps just... Not working."
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-08-05
If I've been using the internet for a while, say three or four hours (which is very little since I spend my life online at the moment), Firefox will stop opening new tabs, windows, or even links on the same page.

 I close firefox when this happens, but then when I try to run it again from the launchers I have absolutely nothing happens. I am writing this in Konqueror (thank the four hells I hadn't uninstalled it yet!) and Firefox refuses point blank  to load up.

 I'll just go check what happens when I go via the command line again, though as far as I recall, it's nothing...

 Yup, nothing:
> raavea@bernard:~$ firefox
raavea@bernard:~$

 No firefox loading or anything. Previously I just rebooted, but it's a little tiresome to have to do it every few hours.

EDIT: That was good. Had to reboot anyway because my system froze up. /swt

---

### Post by kerry_s on 2006-08-05
I would say either your .mozilla profile is corrupt or your firefox is corrupt. First test if it's your .mozilla profile. The .mozilla is a hidden file in your directory rename it to .mozilla.old. Then open firefox it will create a stock .mozilla profile see if you have any problems running it stock. To reverse it just delete the new one and remove the .old from your old one.

For firefox you can down load it from the main site
( [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/) ) click on it to extract. As root open> /usr/lib and look for firefox, rename that to firefox.old, then just copy the new one there, you also need to copy the plugins from the old one to the new one.

Also run memtest firefox uses a bit of memory and there might be something wrong with your ram, just in case.

---

### Post by steve.horsley on 2006-08-05
It may be that there is a firefox process running in the background that's disturbing the next one you launch. Try these next time it freezes:
command: **killall firefox** then launch a new one.
Failing that, try just restarting X with Alt-Ctrb-Backspace.

But neither firefox nor Ubuntu shoudl freeze like that - you may have flakey hardware.

---


---
title: "GNOME keeps freezing after Gutsy upgrade"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by antony_ec on 2008-03-17
I have a Dell Latitude D600 which has been working fine on Ubuntu for a few months. I originally installed Feisty and upgrade to Gutsy last week.

Since then, I've had several problems with the desktop freezing. 

A typical example is when Firefox loads a new window from a hyperlink - the newly opened window freezes and is non-responsive and the top and bottom task panels stop working. The system doesn't completely freeze and strangely enough, the original Firefox window still is responsive, as are certain keystrokes (like Alt-F2 which brings up the Run Application command window).

Even more annoying is that it is an intermittent problem and does not seem to be easily reproducable - in fact I just tried the exact same page which caused the earlier problem (and made me have to reboot) and now everything is working ok....

Wondered if anyone has had similar problems or can advise on anything I can check...

---

### Post by gobbles414 on 2008-03-17
> **antony_ec said:**
> I have a Dell Latitude D600 which has been working fine on Ubuntu for a few months. I originally installed Feisty and upgrade to Gutsy last week.

Since then, I've had several problems with the desktop freezing. 

A typical example is when Firefox loads a new window from a hyperlink - the newly opened window freezes and is non-responsive and the top and bottom task panels stop working. The system doesn't completely freeze and strangely enough, the original Firefox window still is responsive, as are certain keystrokes (like Alt-F2 which brings up the Run Application command window).

Even more annoying is that it is an intermittent problem and does not seem to be easily reproducable - in fact I just tried the exact same page which caused the earlier problem (and made me have to reboot) and now everything is working ok....

Wondered if anyone has had similar problems or can advise on anything I can check...

IMHO, it is better to backup your important data and do a "fresh" install of the new version of Ubuntu than to use the upgrade feature. The one time that I've used the upgrade feature, I encountered similar problems to yours. But if you insist on using the upgrade feature, you might find it useful to run the following maintenance routines in the command line (terminal). Restart your PC once all of the routines have completed successfully:

[I]sudo apt-get --purge autoclean
sudo apt-get --purge autoremove
sudo run-parts -v /etc/cron.daily
sudo run-parts -v /etc/cron.weekly
sudo run-parts -v /etc/cron.monthly[/I]

Did this help?

---

### Post by Cooner on 2008-04-21
I've also had this problem on a D600.  It actually started recently on Edgy, and I upgraded as an attempt to fix the problem (only to see it come right back).  

I can confirm similar behavior (non-responsive toolbars, some things remain clickable but most are not, but typing works just fine, as does keyboard shortcuts.  Alt-F4 closes the window, and things are back to happy normal until I open a new window, at which point we repeat.) with firefox, evolution, and even gnome-terminal.

I recently went for over two weeks of solid usage with no troubles, and suddenly it came back again.

I cannot reproduce anything like this on a second, Windows partition.

I'm trying the above suggestions, and will update later...

---


---
title: "Wine locks after install"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by bandy on 2007-10-29
I have two machines running Ubuntu 7.10.

On one machine wine installed and works beautifully, but on the other machine any attampt to configure, use or uninstall wine completely locks the computer which has then to be rebooted.

The only difference I can find between the two machines is that:

On machine one (which works) the wine directory is shown as .wine

On machine two (which doesn't work) the directory is shown as .wine with a suffix e.g.  .wine - 1jw2345

I have tried removing, purging and re-installing wine on this machine a number times and in each case the wine directory comes complete with a different suffix.

I have also tried fresh installs of Gutsy on this machine but the wine directory with suffix, complete with locking still occurs.

Am I being stupid and not seeing my own errors or is there a real problem that I'm not reaching.

Your assistance would be gratefully received.

---

### Post by arckeda on 2007-10-29
I had the exact same problem!  I solved it by simply downgrading wine, I don't think I will need any new features until 1.0 comes out.

---

### Post by bandy on 2007-10-29
Can you please explain a little more how to downgrade wine

---

### Post by arckeda on 2007-10-29
Not a problem:

Open up Synmaptic Package Manager, in Gnome it is under System, Administration.
Search for Wine.
Select wine.
Click on Package, then Force Version.

Enjoy. :)

---

### Post by Crafty Kisses on 2007-10-29
Uninstall the current version, then reinstall an older version.

---

### Post by bandy on 2007-10-30
Thank you for the comments regarding Force Version, however it is greyed out on my machine and I can't find a way in which to "ungrey" the menu item.

I tried going to the Wine site and downloaded an earlier version but that didn't work - so how far back did you go for your version.

By the way on another thread I noticed that other people suffering from this problem also appear to have S3 Unichrome video systems.   This may therefore be a problem with this inbuilt system.

---


---
title: "updates etc for Feisty Fawn?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by skeletor16940 on 2007-05-25
Hi everyone,

This is probably a silly question, so understanding required.  I have not seen any updates, etc for some 2 1/2  weeks, and of course being just converted from XP which has updates etc every 5 minutes, was just wondering if I have missed anything.  Did have some updates right at the start of FF, am just wondering, perhaps someone can ease my gripe?  Thank you.

---

### Post by spin2cool on 2007-05-25
I've had several updates come through in the last two weeks.

have you modified your /etc/apt/sources.list ?  run 'sudo apt-get update' and see if there are errors.

---

### Post by martinp23 on 2007-05-25
Not a silly question at all, especially when you come from the barrage of updates thrown at you in Windows!

A lot of the fixes for Windows are to patch security problems in their software and the operating system itself.  Fortunately, largely because its code is open to regular review and thorough testing, Linux distributions such as Ubuntu need updates far less often.  The only updates you are likely to require are those to libraries and programs installed on your system.  

The way to tell if updates are waiting is to look to the top right of the screen - if there are updates waiting to be downloaded, there will be a small notification icon which should show a balloon when you start up the system, informing you of updates being available.  If you click the notifcation icon, a dialog will appear which will gude you through the updates process.

As I mentioned above, updates aren't released very often, and when they are, the notification icon should be shown.  Another method to force updates (where available) is to go to System>Administration>Synaptic Package Manager.  There you should click the "Reload" button (to make sure that the system knows what needs updating), followed by the "Mark All Upgrades" button, and then the "Apply" button.  Any software updates will then be applied.

---


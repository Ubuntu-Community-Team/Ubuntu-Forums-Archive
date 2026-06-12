---
title: "Doesn't wake up from sleep AND how can I bypass Grub?"
date: 2009-12-25
forum: Apple Hardware Users
---

### Post by jmagick07 on 2009-12-25
MacBookPro3,1
Ubuntu 9.10

This is a two part question, as you could gather from the title.

Part One:
When I close the lid of my computer, then reopen it a little while later, Ubuntu won't turn back on.  I have to do a hard reset by holding the power key then reboot.  How can I fix this issue?

Part Two:
I set my computer up to triple boot Mac OS X, Windows 7, Ubuntu 9.10
I installed rEFIt to have a nice graphical menu of which system to boot into.  Since I'm using rEFIt, I don't really need Grub as a secondary menu list when I boot into Ubuntu, is there a way to disable it for now, then maybe re-enable it later on if I ever decide to?

---

### Post by tom4everitt on 2009-12-26
Part one:
As a start you should visit
System->Preferences->Power management
and tell it to have a blank screen instead of suspending, when lid is closed. Do this for both battery powered and cable powered. There is no use to put your computer if it never wakes...


Part two: 
Did you install 9.10 from scratch, or did you upgrade from an earlier version? (i.e, do you use old grub or grub 2)

---

### Post by tom4everitt on 2009-12-26
If you want to suspend you can try the following:

first install uswsusp:
sudo apt-get install uswsusp


then try if it works:
sudo s2ram

if it goes to sleep and wake up nicely you can just use this instead of the built-in suspend function. (which mean you will have to type this every time you want to suspend.)

This guide seems to explain how to make it the default suspend script, its a bit old but can be worth a try (backup/remember all the changes you make though, so you can reset them in case it doesn't).

[http://jrobbo.com/blog/?tag=ubuntu-hibernate-suspend-uswsusp](http://jrobbo.com/blog/?tag=ubuntu-hibernate-suspend-uswsusp)

---


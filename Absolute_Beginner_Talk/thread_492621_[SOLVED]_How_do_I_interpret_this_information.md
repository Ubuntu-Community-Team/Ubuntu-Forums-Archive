---
title: "[SOLVED] How do I interpret this information?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Ambidextrous on 2007-07-04
I've been using Ubuntu (7.04) for about a month.  My pc experience started with DOS 3.3, so I'm familiar with a CLI and not intimidated by it.  In my quest to be self-reliant I've been RTFM-ing like a fiend.  A lot of it has helped.  There are some very useful guides out there.

One made the following suggestion in order to get a better grasp of what's actually installed, and exactly where its components are:

"Install the Debian menu. The Debian menu has a much more thorough list of your installed applications, and it will be available as a category in your existing Applications menu. You need to install the package called *menu-xdg* and possibly restart X (ctrl + alt + backspace) for it to show up."

So I did, using Synaptic, but I cannot persuade the debian menu to show up in my Applications menu.  When I examine its properties in Synaptic, the Dependencies tab gives me the following information:

**Recommends:**  menu
**Conflicts:**  menu (<2.1.14)

I don't know how to interpret this, but I have a suspicion that "Conflicts" might not be good news.

If someone can explain what it means, and/or how to make the Debian menu appear, I'd be very grateful.

TIA

Terry
[IMG]http://ubuntuforums.org/home/terry/Desktop/Screenshot-synaptic.png[/IMG]

---

### Post by Vajra Vrtti on 2007-07-05
> Recommends: menu
Conflicts: menu (<2.1.14)
It means that the package **menu-xdg** recommends, but does _not_ require, the package **menu**.
However, if installed, the version of the package **menu** must be **2.1.14** or above.

That's OK, because the version of **menu** in Ubuntu 7.04 is **2.1.32**.

---

### Post by Ambidextrous on 2007-07-05
So that's NOT why the Debian menu is reluctant to make an appearance on my Application menu.  Anyone have any theories?

Terry

---

### Post by Moop on 2007-07-05
Right click on Applications and choose edit menus. If Debian is listed there you can put a check in the box to add it to your menu.

---

### Post by Ambidextrous on 2007-07-05
Thank you, but I already tried that.  Check-mark in the Debian box notwithstanding, it resolutely refuses to appear in the Applications menu.  And unlike the other available choices, the text doesn't change from the inactive italic to the slightly larger, normal, active font.  The  box un-checks itself too.

Anyone else?  This really ought to work.

Terry

---

### Post by CaptainInsaneO on 2007-07-05
Are there any items actually IN the debian menu? I know if I want to display a menu that has no items, it won't allow me, don't know if that's the case for anyone else though.

---

### Post by Ambidextrous on 2007-07-05
You nailed it Captain.

In my ignorance/naivete (this editor won't allow accented characters), and from the description in the how-to, I had assumed that the Debian menu, once installed, would take an inventory of my installed applications and insert them.  Apparently this is not the case - or if it is, I can't find the command.

Once I manually added an application the Debian menu dutifully appeared in my Applications menu.  After all that, it's a bit under-whelming.

Thanks

Terry

---

### Post by dpar on 2007-07-05
I have menu-xdg as well as menu installed. Mine showed up with all the apps listed. Menu may be needed in order for Debian menu to get all the listing.

---

### Post by Ambidextrous on 2007-07-05
I seem to have marked the thread "Solved" just a bit too soon!

I have Menu installed.  However, I found a broken link in one of the menu-xdg folders.  I think I'm going to completely uninstall it, reboot then reinstall.  (Can you tell I'm used to working with Windows?)

---

### Post by CaptainInsaneO on 2007-07-06
Personally, I'd prefer to stay with the GNOME layout instead of making it look like Windows, but hey. Your computer, your choice. :)

Can you please explain what you mean by "broken link"? Maybe we can fix you without you having to go though a whole uninstall-reinstall.

---

### Post by Ambidextrous on 2007-07-06
I didn't say I _liked_ working with Windows...

I just meant that uninstalling the troublesome software, rebooting then reinstalling it was the standard Windows "fix".

Thanks for the offer, but I already fixed it:  I was led to believe, by one of the early replies, that Ubuntu shipped with menu installed.  Mine didn't, and even though the properties tab for menu-xdg (Debian menu) only lists it as 'recommended', I can state with some authority that menu-xdg works a whole lot better with it installed.

I uninstalled mnu-xdg, installed menu then reinstalled menu-xdg.  After a full reboot (restarting X didn't cut it) the Debian menu was installed in my Applications menu and was fully populated and functional.


The author of the how-to was correct:  Debian menu shows a lot more applications than the default Gnome menu.


What I meant by "a broken link" was just that.  There was a link in one of the menu-xdg folders marked as "broken".  It pointed to an executable in another folder that didn't exist.  Actually, it didn't exist anywhere on my system Nautilus could search.  I suspect that it was installed when I installed menu, but I haven't checked.  For now, it just works. ;)

---

### Post by CaptainInsaneO on 2007-07-07
Well congrats on gettin it fixed! :popcorn:

---


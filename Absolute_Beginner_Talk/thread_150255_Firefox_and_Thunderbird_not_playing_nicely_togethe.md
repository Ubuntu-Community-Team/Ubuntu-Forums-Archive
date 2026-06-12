---
title: "Firefox and Thunderbird not playing nicely together"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by words1 on 2006-03-25
Ubuntu 5.04.  Firefox 1.5.0.1 and TBird 1.5, both installed through Automatix.  Both are selected as "preferred applications."

Two odd problems:

1)  When I click on a link in a mail message in TB, FF does not open the page.  

2)  When I right click on a page in FF and "send link" when TB is already open, a new instance of TB opens along with the mail message to send.  How do I stop it spawning a new instance of TB?

Any help will be greatly appreciated.

---

### Post by dcstar on 2006-03-25
[QUOTE=words1]Ubuntu 5.04.  Firefox 1.5.0.1 and TBird 1.5, both installed through Automatix.  Both are selected as "preferred applications."

Two odd problems:

1)  When I click on a link in a mail message in TB, FF does not open the page.  

2)  When I right click on a page in FF and "send link" when TB is already open, a new instance of TB opens along with the mail message to send.  How do I stop it spawning a new instance of TB?

Any help will be greatly appreciated.[/QUOTE]
Applications-System Tools-Configuration Editor-Desktop-Gnome-url-handlers

Check mailto, http and https entries.

---

### Post by aysiu on 2006-03-26
Take a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=60427).

---

### Post by words1 on 2006-03-26
[QUOTE=aysiu]Take a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=60427).[/QUOTE]
That fixed problem #1, but problem #2 (spawning a new instance of TB) is still happening.

[I]Applications-System Tools-Configuration Editor-Desktop-Gnome-url-handlers

Check mailto, http and https entries.[/I]

All three are enabled.

---

### Post by words1 on 2006-03-26
SUCCESS!

Under 

Applications-System Tools-Configuration Editor-Desktop-Gnome-url-handlers

the "mailto" key was set to 

mozilla-thunderbird -mailto %s

I removed the "-mailto" (making it just "mozilla-thunderbird %s") and it no longer spawns a new instance of TB.

Thanks for all your help!

---


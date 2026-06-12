---
title: "Broken Filter"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Zotick on 2008-03-16
To fix the broken filter dependencies, do I have to insert the ubuntu cd?

---

### Post by PeterJS on 2008-03-16
Only if you don't have an active internet connection. You should be able to get all the package updates you need to fix breakages online.

---

### Post by Zotick on 2008-03-16
Yeah but this one is telling me to put the ubuntu cd in, I'm just wondering if theres any other way instead of having to put the ubuntu cd in.

---

### Post by beercz on 2008-03-16
Not necessarily, it depends on your sources.

In synaptic, click on the Status button (bottom-left) to find all your broken packages.  You can then right-click on the broken package and choose remove.

If you need any more help, then let us know which package(s) is/'are causing the problem and any messages concerning broken packages you see.

---

### Post by Zotick on 2008-03-16
The 2 things that are showing are

**intltool** and **libstdc++6-4.1-dev**

This is stopping me from letting me download anything or being able to update my computer.

---

### Post by PeterJS on 2008-03-16
> **Zotick said:**
> Yeah but this one is telling me to put the ubuntu cd in, I'm just wondering if theres any other way instead of having to put the ubuntu cd in.

Looks like your sources list is also bad then, because the CD should be removed from the list when the install completes. I'd bet you didn't have an active internet connection when you installed the system, and my favorite gutsy bug of assuming the internet doesn't exist is showing up.

Go to System > Administration > Software sources, and make sure that all 4 repositories on the front tab are enabled, and disable any CDrom entries on the front tab, or the third party tab.

---

### Post by Zotick on 2008-03-16
[IMG]http://i25.tinypic.com/21mcle0.png[/IMG]

So you want me to un-check** cdrom with ubuntu 7.10 'Gutsy GIbbon'** ?

---

### Post by PeterJS on 2008-03-16
Yep, and a thumbnail with less table brakeage whould be nice. The main and restricted repositories above provide the same software, only more updated versions.

---

### Post by Zotick on 2008-03-16
Dude you are a genius, one more question, how do I find out if im updated or not, I accidentally removed the update icon on my task bar and now I don't know if im up to date or not.

---

### Post by PeterJS on 2008-03-16
If the update icon is missing there are two possible reasons why:
1) You're up to date so it's not needed
2) You removed the entire notification area, and have no system tray.

For the latter, right click somewhere on the panel about where you want the notification area to be, and select add to panel, and then add a new notification area. After it's added you can right click on it's left edge, and select move and drag it where ever you want it.

A more manual way to check for updates would be to load up synaptic, and reload the package list (ie update the list of what's available), and then check the installed (upgradeable) filter under status, note the filter won't exist if there is nothing that needs upgrading.

---

### Post by Zotick on 2008-03-16
Thanks

---


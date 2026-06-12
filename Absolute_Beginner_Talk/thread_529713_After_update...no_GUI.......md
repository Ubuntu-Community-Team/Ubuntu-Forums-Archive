---
title: "After update...no GUI......"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by rallenk on 2007-08-19
After update from within Fiesty from 7.04 to 7.2, upon restart I get no user interface and this is what It tells me :
"Failed to start x server. It is likely it is not setup correctly. Would you like to view x server to diagnose problem?"
I enter 'yes' ....I find these errors and warnings...

(ww) open ACPI failed
(ee) module ABI minor version (2) is newer than servers version (1)
(ee) no drivers found

"Fatal servor error: no screens found"
I then enter on "OK" and get this:

The x server is now disabled. Restart GDM when it is configured correctly.

So, what needs to be done?

This was an automatic Update from my panel inside Fiesty 7.04

Help please....:confused:

Bob
__________________

---

### Post by kidcharles on 2007-08-19
One thing that seems strange is you are referring to version '7.2' which doesn't really make sense. Ubuntu is on a 6 month release cycle and the version refers to the year and the month (7.04 came out in April, 2007). If you did an automatic update within Feisty it probably just installed the latest versions of all the packages (programs, libraries, etc.) and you are still using 7.04.

It is possible something done during this update did something that is making your X not work (that's the graphical desktop). Given that error message, I found this in a Google search:

[http://matrox.tuxx-home.at/viewtopic.php?p=493&sid=ee02dc24367622a0079d6e5c73d0e83e](http://matrox.tuxx-home.at/viewtopic.php?p=493&sid=ee02dc24367622a0079d6e5c73d0e83e)

The link suggests starting X with the command:

```

startx --ignoreABI

```

Try that and see what happens.

---

### Post by alienexplorers on 2007-08-19
You would not have been trying to update to Gutsy Gibbon 7.10 were you.  You know that is only in testing phase.

---

### Post by sdowney717 on 2007-08-19
i had this problem after uninstalling the ATI driver that was installed using ENVY


So I booted to the command prompt
Then I ran ENVY text mode, reinstalled the ATI driver and it works again
Is Envy in the default repos?

scott@scott-desktop:~$ sudo apt-get install envy
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
envy is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---


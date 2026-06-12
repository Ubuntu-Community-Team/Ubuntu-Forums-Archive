---
title: "The only way I can really shutdown is...."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-12-12
...is to click on "Restart" and  it'll really "shutdown"... so to speak.

I mean that as soon as it restarts and that I see the screen with the name of my computer + boot options, I power off manually.

I think this is much less harmful to both my OS and HW than to power off manually more or less any time during the shutdown process.* Am I right there?*

Note that I've tried just about everything else mostly found on ubuntuforums.org.
Thnx for reading. Any ideas' welcome.

---

### Post by Sef on 2007-12-12
Have you checked the Power Management settings in the BIOS?

---

### Post by PmDematagoda on 2007-12-12
Did you also try shutting down manually using:-

```
sudo shutdown -h now
```

> I think this is much less harmful to both my OS and HW than to power off manually more or less any time during the shutdown process. Am I right there?

Yes, I believe you may know what could happen if the drives are still mounted when you power off manually. It is less harmful when you power off the system manually while it is starting up, but it still can cause a bit of damage in the process.

---

### Post by meindian523 on 2007-12-12
what about ```
sudo init 0
```that's a zero,not an "oh"

---

### Post by snickers295 on 2007-12-12
[FONT=System]try looking in the power management in the bios and if the shutdown won't work then try those commands.
if those commands do work, report a bug at launchpad about it (and if those commands don't work, report a bug about that).
[/FONT]

---

### Post by viking777 on 2007-12-12
I have lived with this problem for over a year. I have investigated it fully, tried every 'fix' out there, posted bugs on Launchpad and all the other things that you are supposed to do. The long and short of it is that until the Linux kernel has acpi modules that are as functional as windows ones you will never be able to shut down cleanly on some machines.

To me, since I am affected by it, it is the most pressing problem in the Linux world, but unfortunately xyz, you and I are in a minority, for most people 'wobbly windows' are vastly more exciting, until that fad is over, if you want to use Linux, you are just going to have to live with it.

And that is a big big bummer!!!

---


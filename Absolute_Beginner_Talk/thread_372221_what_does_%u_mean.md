---
title: "what does %u mean?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by anselm1109 on 2007-02-27
I recognize that this must be some sort of variable, but when I look at the properties of various icons that launch programs they all seem to have something like "firefox %u". What does this mean?

If I want to create a custom icon for a program should I include it.

Mostly I'm just curious.
Thanks!

---

### Post by kerry_s on 2007-02-27
No, all you need is "firefox" if you include it it will try and find the web page for %u.

---

### Post by FyreBrand on 2007-02-28
> **anselm1109 said:**
> I recognize that this must be some sort of variable, but when I look at the properties of various icons that launch programs they all seem to have something like "firefox %u". What does this mean?

If I want to create a custom icon for a program should I include it.

Mostly I'm just curious.
Thanks!It's only for menu shortcuts and not the command line.  For menu shortcuts %u means "a single url".  That is the application is executed with a single url following.  It will probably work fine without it and shouldn't hurt to add it.  If you are configuring a shortcut that executes firefox from the terminal then %u will be the url it goes to.

---

### Post by mcduck on 2007-02-28
Having the %u in a desktop or panel launchers allows you to drag files to the launcher to open them in that program. So the %u is replaced by path/url to the file you dragged to the launcher.

Using it only makes sense for some programs, and it's not really needed so you can remove it if it causes troubles to you. 

For some people having the %u in firefox launcher causes FF to try to open page '%u', but it has never happened to me so I prefer to keep it there :)

---


---
title: "Installed application not found?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by ellster456 on 2007-10-01
OK I know there's a million threads out there called this and I tried suggestions in a good many of them with no results. Only thing I haven't tried is the Debian suggestion because the link didn't show up to me. 

The applications are dvd-slideshow and spork-perl that I got from Synaptic Package Manager. One other didn't show up as well but I don't know its exact name right off hand. SPM says all of these are fully installed and all and says they're in usr/bin or usr/share I think but I've typed both of those and the names into Terminal and nothing happens. 

I tried using locate and didn't get a bash with that one but nothing happend either.

---

### Post by skyjacker on 2007-10-01
> **ellster456 said:**
> OK I know there's a million threads out there called this and I tried suggestions in a good many of them with no results. Only thing I haven't tried is the Debian suggestion because the link didn't show up to me. 

The applications are dvd-slideshow and spork-perl that I got from Synaptic Package Manager. One other didn't show up as well but I don't know its exact name right off hand. SPM says all of these are fully installed and all and says they're in usr/bin or usr/share I think but I've typed both of those and the names into Terminal and nothing happens. 

I tried using locate and didn't get a bash with that one but nothing happend either.
Try typing whereis [filename] in terminal. File name is the name of the program you are trying to find.

---

### Post by ellster456 on 2007-10-01
Ok I was able to find them in their respective folders... but when I click on them it doesn't launch. If it matters the extension is .gz but I did get them from SPM so they should work right?

---

### Post by Perfect Storm on 2007-10-01
```
spork
```
in the terminal.

More info:
```
man spork
```

---

### Post by rsambuca on 2007-10-01
Did you look for them in the applications menu?  If you installed using Synaptic they should have a launcher in the menus.

---

### Post by Perfect Storm on 2007-10-01
It's a CLI application.

---

### Post by ellster456 on 2007-10-02
So far no luck. I even looked at the Installing with Ubuntu help guide for CLI and tried using those steps to no avail.

---


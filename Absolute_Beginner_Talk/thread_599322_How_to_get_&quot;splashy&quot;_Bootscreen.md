---
title: "How to get &quot;splashy&quot; Bootscreen"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by fert on 2007-11-01
Hello there,

I have the following version of Ubuntu: Ubuntu 2.6.20-15-server 
My problem is that I do not have something alike the "Live CD", I only have the server edition by me.

I managed to install KDE successfully, because no GUI was present, I also don't have many of the normal GUI things, and including, I do not have "splashy", the boot screen util.

I tried to get it trough the "apt-get" command, it downloaded, and installed, i think.
When I tried the command "splashy", my screen just goes blank for about 5 seconds, and then return to the desktop.

When I shutdown, it is just a flashing underscore at the top-left of my screen.
If I press Ctrl+Alt+F7, the normal comes back up, eg. Shutting down messages.

When I boot up, I get the normal GRUB loader screen, and then when linux begins to boot, It shows "Starting up..." (or something similar) and then switches to then the screen goes black.
IT then troughs out an error saying that something is missing, I can only remember this location.
```
/etc/inittab/
```
I tried to change the "vga=x" in the grub menu list, but it still happens.

I have goggled, and searched this forum but can't find the correct help.
So I thought I'd post here.

Any and all help is appreciated.

---

### Post by gate on 2007-11-01
If you are looking for all the functionality of Kubuntu, there is a metapackage called kubuntu in the package managers. that *should* get you all the features you are looking for.

 I did find this message archive that should help: [http://ubuntuforums.org/archive/index.php/t-11478.html](http://ubuntuforums.org/archive/index.php/t-11478.html)

---

### Post by fert on 2007-11-01
Thanks for replying.
But unfourtianitly, I'm not able to download such big packages, due to bandwith here.
Is there perhaps another way?

---


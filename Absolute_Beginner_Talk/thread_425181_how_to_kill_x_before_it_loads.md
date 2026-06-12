---
title: "how to kill x before it loads?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by leandra on 2007-04-27
I've just installed ubuntu 7.04 on a new machine (amd64, M2V-MX / k8m890 chipset) everything went fine and everything looks fine until about 2 seconds after x/gnome has loaded. Then the screen flickers insanley and my machine locks up (no i/o with keyboard/mouse).

I've fiddled with the BIOS settings to see if 'graphics aperature size/gp mode/primary grapics adapter' settings make any difference, but they seem not to.

I'd like to "kill x" before it loads so that i can try fiddling with the x config files. How do i tell if it's 'cause i'm missing a driver?

---

### Post by Cypher on 2007-04-27
When you get the GRUB boot loader, choose to EDIT the command line and add the word "single" to the end of the boot parameters. Now boot Ubuntu and this will drop you to a shell where you can fix whatever is ailing your installation.

---

### Post by leandra on 2007-04-27
WHOOO HOO!

Thanks for the tip. All I needed to do was reduce the default depth to 16 in xorg.conf 

Yay! Annoying that I didn't think to do this first. ;)

---

### Post by leandra on 2007-04-27
doh. that wasn't it. :(

now it seems that xorg works fine when started from 'single' mode. but crashes when i just boot up the machine.

---

### Post by Hendrixski on 2007-04-27
I hope you read the documentatino about this kind of thing.  There are plenty of people who have written about how to fix this better than I can.

Generally, whey you change a file like that, you want to create a backup, so that you can restore it in case something goes horribly wrong.

By the way, welcome to the Ubuntu community.  We hope you like it here, and get involved in some of the fun stuff we do.  Be sure to check out the Ubuntu Loco team for your area, so you can share fun times with other Ubuntu users live.

---

### Post by whee on 2007-04-27
Are you sure this is an X problem and not a Gnome problem?
Also did you do a clean install of Feisty or did you upgrade?

---

### Post by leandra on 2007-04-27
thanks for the responses guys.

well, i've been using linux for about 5yrs now, so i'm confident chainging config files and getting them back if necessary.

not certian it's an x problem as opposed to a gnome problem. just a huge hunch. why/what would gnome be doing to 'cause my system to crash? ie: what should i look for? the log files don't seem to have anything out of the ordinary in them.

... except for an: (EE) AIGLX: Screen 0 is not DRI capable 
... which I'm trying to solve, but from what I've been reading, x can ignore that error and still work right?

---


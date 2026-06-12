---
title: "permission to edit files"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by buntolith on 2006-09-15
Hi,

I have just installed ubuntu, actually I have done it three times while I have been playing around. Before I partitioned the harddrive I backed up my personal data onto an external harddrive. I have 4 partitions in total, WXP, Root, swap and /buntolith and I want to use /buntolith to store personal stuff. When I tried to copy all my personal data from the external harddrive onto /buntolith it is not possible to choose paste because I don't have permission. It says "You are not the owner, so you can't change these permissions". On my previous installs I didn't have this problem, and I do not want to make do another installation even though it is easily done. I want to deal with this problem with your help instead. Can somebody please help me out. *beg*

I am a newborn ubuntu baby with the ability to read. I will understand some basic instructions...

---

### Post by Druidor on 2006-09-15
Well you could always use the ***gksudo Nautilus*** command to do a graphical drag & drop but this will not solve the problem of the destination being root privaleged in the first place

but that is tyour best bet on getting the files back into the machine from the external HD.

---

### Post by ciscosurfer on 2006-09-15
Hit ALT-F2, a dialog will popup, enter: [COLOR=SeaGreen]gksudo nautilus[/COLOR]
This will open nautilus with root permissions...try the move again once you've done this...you can also create a launcher on your desktop so you only have to click it and the dialog will open: on the desktop, right-click and choose "Create Launcher"...Enter a name like [COLOR=Indigo]Root Nautilus[/COLOR] and enter the [COLOR=SeaGreen]gksudo nautilus[/COLOR] as the command.

You can also modify permissions for the directory that you don't have permissions on this using 'chown' or 'chmod'

Read the man pages for further explanantion; in a terminal type```
man chown
man chmod
```

---

### Post by buntolith on 2006-09-15
I don't think I have Nautilus installed so nothing happens. Anyway, I'd rather take the goat by the horns and try to solve the problem properly so that I can use the file browser instead. Thanx for the help anyway...

---

### Post by buntolith on 2006-09-15
Thanks ciscosurfer. That started the nautilus program and I had permissions to do the copy. I will try the other commands later and I'll come back with the result...

---

### Post by ciscosurfer on 2006-09-15
Glad that helped.  We're always here to help with any questions you have; don't be fearful of asking...everyone at some point was new to Linux (and of course, Ubuntu << pronounced oo-boon-2)

---


---
title: "So how does Linux work?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Rhumbline on 2007-08-08
I want to know more about what happens with Linux. For example, when I boot up, does it remember my last config or does it find everything anew each time? 
I have a CD ROM drive which works fine, even though it doesn't appear in my 'places' list ( I have 2 floppy drives there even though there's only one in the machine). 
I want to add a DVD drive I have. I connected it up but it didn't show up and I can't use it, how do I install it?

---

### Post by Jimmyfj on 2007-08-08
Ubuntu remembers all my settings all the time - Just make sure you do not confuse an install with the use of the Live Cd. Settings are not remembered in a Live Cd because you run that from RAM not the hard drive.

---

### Post by asmoore82 on 2007-08-08
the CD drive shouldn't show up in "Places" ... it should be under "Computer" ...
which can be reached from "Places"

this Drive you are adding ... make sure it shows up in your BIOS settings ...
you are familliar with pin settings, CS/Master/Slave, yes?

---

### Post by p_quarles on 2007-08-08
I believe that if you add a drive after installing Linux, you need to manually configure your system to mount that drive at startup. There was a very recent thread about this here, but it was about a hard drive rather than a DVD drive. I'll do a quick search for it.

EDIT: Here's the thread:
[http://ubuntuforums.org/showthread.php?t=519920](http://ubuntuforums.org/showthread.php?t=519920)

---

### Post by proalan on 2007-08-08
> So how does Linux work?

very well thank you

---

### Post by vexorian on 2007-08-08
If you had the CD drive while you installed  and you also can see it under "computer" then whenever you place a disk it will be mounted and will be shown on the desktop.

---

### Post by Rhumbline on 2007-08-08
Thanks, I should be able to get some clues from that.

---

### Post by Rhumbline on 2007-08-08
Yes I know about the jumpers, but do I set it as a master or slave or what?
Is the BIOS separate from the OS?

---

### Post by asmoore82 on 2007-08-08
> **Rhumbline said:**
> Thanks, I should be able to get some clues from that.

if the drive shows up okay in your BIOS but still not in Linux the next step
would be to add an entry for it to your "/etc/fstab" file.

---


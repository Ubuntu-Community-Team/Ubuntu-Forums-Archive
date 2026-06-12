---
title: "[SOLVED] First frazzled hours -- 1 question for starters"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by cathuria on 2007-10-30
Greetings!
After a stressful day & a half of backing up and disk-scrubbing, I've got a dual-boot of Gutsy and XP running.  I even got my beloved Wacom tablet to behave properly, although I'm still struggling to match up the fglrx drivers with my Dell monitor.  
But my first question will be a minor annoyance that should be easy to solve.  Every time I go into Ubuntu, two windows partitions are mounted automagically (the main XP partition and some Dell utility partition).  I'm not allowed to unmount them, but I suppose I could "sudo" something to do that (Sudo throw? Sudo chop?).  But the most annoying thing is that the dang icons are plopped on my desktop and I can't seem to delete them.
So, how do I keep those icons from popping onto my desktop, or how do I stop the partitions from being mounted on boot?
Thanks!

---

### Post by adidalax on 2007-10-30
Still new to Ubuntu here, but most Linux distributions use the /etc/fstab file to specify volumes mounted at boot. Start there and try commenting out the lines that have FS Type as NTFS in there.

With Ubuntu, it automatically sets up a sudoers file, so most administration is done through sudo. Since most of the stuff in /etc is all "system" stuff, you'll need to do "sudo vi /etc/fstab" to edit it.

---

### Post by cathuria on 2007-10-31
Thanks!
I read up on fstab a bit and tried changing a few options, but just commenting the whole thing out seems to the most convenient compromise. (woah... flashback to hacking away at config.sys files...)
 And by goodness is this forum ever busy -- I don't envy the mods -- but hey, I've got my hands full just figuring out Linux.  See ya!

---

### Post by volksman on 2007-10-31
DO NOT comment out everything in fstab.  You will loose your drive mounts (IE /) after a reboot and you will have to use a rescue cd to fix it.

if you just want the icons to disappear from the desktop do this:

```
gconf-editor
```

run that command....then go to Apps -> Nautilus -> Desktop

Remove the checkmark from Volumes_Visible

That will remove them from your desktop.

---

### Post by pjones0404 on 2007-10-31
^^^^^beat me to it. lol


i am pretty sure that u can install gconf-editor and edit the config w/ that.

let me look and see if i can find it. it would be under the nautilus portion of it. nautilus is what draws the desktop on the screen.

found it. u need to open a terminal and run gconf-editor. once this up select apps-nautilus-desktop. there is a check box for volumes visible.

---

### Post by cathuria on 2007-10-31
Well, I didn't comment out *everything...* my goodness, I may be a newbie to Linux but I'm not a newbie to hacking OS's in general:)
But thanks for the tip about the gconf-editor -- that sounds useful!

---

### Post by fouadaslam on 2007-11-03
> **volksman said:**
> DO NOT comment out everything in fstab.  You will loose your drive mounts (IE /) after a reboot and you will have to use a rescue cd to fix it.

if you just want the icons to disappear from the desktop do this:

```
gconf-editor
```

run that command....then go to Apps -> Nautilus -> Desktop

Remove the checkmark from Volumes_Visible

That will remove them from your desktop.

thanks, it worked
cool

---


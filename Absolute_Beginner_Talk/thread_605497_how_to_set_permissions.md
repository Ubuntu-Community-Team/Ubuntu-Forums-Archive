---
title: "how to set permissions?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by littleasian on 2007-11-07
hi guys

im trying to get a new skin for my exaile music player.  directions tell me to transfer the patch to the -/exaile/exaile.theme location

however, when i drag it to the folder, it says i dont have permission to do so.

as far as i'm concerned im the only user and i've been changing things like crazy on this computer.

how do i get permissions to edit this folder???

thanks!

---

### Post by Harpoon on 2007-11-07
I don't have this installed, but are you sure it doesn't tell you to copy 

to the ~/exaile/exaile.theme location and not -/exaile/exaile.theme location
?

~ shortcuts to the /home/username directory for which you do have permissions.  Of course, you can move using /home/yourusername/exaile . . 
Same thing

Otherwise, in a terminal the command is chown, and either -h or --help will tell you what to do.

---

### Post by Griffiss on 2007-11-07
type

```
gksudo nautilus
```

into a terminal. this will bring up a file manager with root permissions. you'll then be able to edit the folder contents and its permissions setting by right-clicking on it.

---

### Post by hyper_ch on 2007-11-07
Griffiss:

I think harpoon is right that the TO didn't enter the right location for the settings.

---


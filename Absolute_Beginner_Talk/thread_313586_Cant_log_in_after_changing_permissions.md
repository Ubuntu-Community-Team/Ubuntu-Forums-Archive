---
title: "Cant log in after changing permissions"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-12-06
Hi,
I had a problem with permissions and was flicking through forums banging in commands as you probably shouldn't do, below is a list of them:

chmod g+w usbdisk
chown -R root: peter /usbdisk

and a couple more that I can't find.
The error message I am getting when I try to log in is:
users HIME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users HOME durectory must be owned by user and not writable by other users.

I can get a terminal throuhg recovery mode so any help I would be very grateful for!

---

### Post by jimbren on 2006-12-06
Try taking ownership of all files in your home directory.

```
sudo chown -R yourusername:yourgroupname *.*
```

---

### Post by peterj on 2006-12-06
says it can't access *.* , what would the default group name be?

---

### Post by Malac on 2006-12-06
If you're not comfortable using the command line.
You can get to a root terminal from the GRUB screen by choosing (recovery mode) then type "startx" and this should log you into a root desktop. I find this more useful.

You should then be able to alter permissions on folders or files through the right-click menu.

Hope this helps.

---

### Post by peterj on 2006-12-06
Nice thanks, I'm nothing special with terminal just basic commands. Its which group I'm in that I'm unsure, It won't let me edit system configuration in startx.

---

### Post by peterj on 2006-12-06
Ah I can log on now normally thanks, but now I get

'internal error
failed to initialize HAL!

Time for a format and re-install anyway, as a newbie I accept my innate ability to render a box useless...

---


---
title: "Copy cd"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by dbusley on 2007-02-27
I recently tried to copy a cd by right clicking it on the desktop and clicking "Copy Disc." It seemed to work fine and then it got right to the very end of making the CD image with very little to go and just froze with no error message or anything. I had to cancel it. Why is this happening? Am I missing a package perhaps?

---

### Post by madcow72 on 2007-02-27
Doesn't sound like you're missing a package, otherwise it probably wouldn't have even begun.  Are you sure the disk isn't write protected or damaged?  Maybe try another disk that you know to be in good condition to rule out any software issues.  

Another great command you could try is the "dd" command to create an .iso image of the disk.  For example:
```
dd if=[COLOR="DarkGreen"]/dev/hdc[/COLOR] of=/home/[COLOR="Red"]user[/COLOR]/Desktop/[COLOR="Blue"]Image.iso[/COLOR] bs=2048 conv=notrunc
```
where [COLOR="DarkGreen"]/dev/hdc[/COLOR] is the route to the drive holding the cd you want to copy, [COLOR="Red"]user[/COLOR] is obviously your user name and [COLOR="Blue"]Image.iso[/COLOR] is the name that you wish to call the CD image, which will end up on your desktop.  This command can take more than a few minutes to complete, so don't close your terminal early thinking it stopped responding.

Once you have the .iso image, you can burn it to cd with k3b or gnome baker or whatever.  Good luck!

---


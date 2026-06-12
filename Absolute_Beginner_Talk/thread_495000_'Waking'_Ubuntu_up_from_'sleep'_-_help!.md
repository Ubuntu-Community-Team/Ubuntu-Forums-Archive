---
title: "'Waking' Ubuntu up from 'sleep' - help!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by staib on 2007-07-07
Thanks for reading this!  I have 2 users on 7.04 - me and my son. If I leave the PC unattended and it's logged in to me, the PC seems to go so deeply to sleep that I need to re-boot.  But if left logged in to my son, after a while it also goes to sleep, but awakens immediately with a shake of the mouse - as you would expect...

What should I check first? 

My System > Preferences > Screensaver > Power Management has been set to 'Never' go to sleep - but that doesn't seem to do anything!

Nick

---

### Post by macogw on 2007-07-07
Is it a laptop (open or closed?) or a desktop?  Is there a difference in the amount of time each of you walk away from the computer (half hour v. 6 hours)?  

If you want to make it never standby/hibernate, you can edit /boot/grub/menu.lst ("sudo gedit /boot/grub/menu.lst") and add noacpi at the end of the "# defoption=" line then "sudo update-grub"  Removing that addition from it and re-running "sudo update-grub" will take it back to normal, so if you ever decide to add power management, you'd do that.

---

### Post by staib on 2007-07-07
Thanks for the reply.  It's a desktop PC.  It goes to sleep after at least an hour of inactivity - I am reluctant to remove the functionality as it seems to work fine if the other user is logged on or if we are both logged out.  

On balance I should just always remember to  log out, but you know what it's like - phone goes, you get distracted and <yawn> - time to reboot!

Thanks again - I appreciate the commands (which I've saved, just in case!)

---


---
title: "Lost Data?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Kymac on 2007-11-04
Ok, I came home this weekend from college.  I decided to upgrade the family computer that I outfitted with Ubuntu before I left from 7.04 to 7.10.  Everything seemed to be working fine, and I left it alone for awhile, when my father said something was wrong.  Supposedly some window about settings came up and he clicked 'Replace' and then tried to switch user, but the login screen never came up, the screen just remained black.  Therefore, he shutdown the computer.

I'm not that great at troubleshooting, but I was wondering if there was some way to fix this w/o losing the data on everyone's account.  If there is not, is there a way I can put the harddrive in a different computer, and extract the data from this harddrive to the computer's harddrive.

Thank You for your help, Kymac.

---

### Post by SOULRiDER on 2007-11-04
Have you tried logging in and continuing the installation?
Log in and do a
```
sudo dpkg --configure -a
```

After that I suggest you do
```
sudo aptitude update
sudo aptitude dist-upgrade
```

You can do this from a terminal as your regular user, but if for some reason you cannot boot correctly use a recovery console but dont add sudo to the commands.

---

### Post by Kymac on 2007-11-04
I can't log in at all.  When I turned the computer back on, the Ubuntu loading screen loads, and then there is just a blank, black screen.

---

### Post by SOULRiDER on 2007-11-04
Have you selected recovery mode in GRUB?

---

### Post by Kymac on 2007-11-04
I'm not to computer swavy, instead of the basics (installing an OS, putting together the hardware, ect.)  Ubuntu was reccomended to me by a friend.

I'm not certain as to what you mean.  Do you want me to use a live disk and attempt to finish the update from there?

---

### Post by SOULRiDER on 2007-11-04
No, do you ever get a screen where you can select what kernel it is you want? If so you have to select recovery mode and run those commands there. If youre never asked for a selection keep your eyes open for a message saying "To load grub press esc now" or something similar, whne you see it press esc and select recovery mode.

Id like to continue helping you but its almost 4 am, time to go to bed :P

---

### Post by Kymac on 2007-11-04
Ok, Thank You very much.  I greatly appreciate it, I'll keep my eyes open and try it out tomorrow morning.

---

### Post by Kymac on 2007-11-04
Ok, I tried what you said, and then when I attempted to get on, instead of a blank screen, I get an error box that says 'The greeter application appears to be crashing.  Attempting to use a different one'.  Then I click ok, and the same thing happens.

Is there a way to fix this?

Also, I have another computer, but I want to keep the same home directories for everyone (as far as data, settings, ect.).  If I add the hard drive to a computer as a second hard drive, how can I extract the home folder?

Thanks for your help.

---

### Post by Kymac on 2007-11-06
Any Ideas?  This weekend I'm driving back home and have to retrieve the data that was on that computer.

---


---
title: "Tried Ubuntu Live On Imac G3 - No Go"
date: 2006-07-31
forum: Apple PPC Users
---

### Post by cannuck on 2006-07-31
Tried to use Live Ubuntu on a iMac G3 - went thru series of OKs and then black screen and no go. What to do!

---

### Post by linear on 2006-07-31
The Live CD does not set up xorg.conf properly for the iMac G3.

After booting is complete,
1. **ctrl-option-F1** (should give you a command prompt - may take a few tries)
2. type: **sudo nano /etc/X11/xorg.conf** (return)
3. make your edits (see below)
4. **ctrl-O** (return) to write edited file
5. **ctrl-X** to exit nano back to command line
6. type: **sudo /etc/init.d/gdm restart** (return) to restart Gnome (note: with the Dapper Live CD, use **sudo killall -HUP gdm** if Gnome won't restart.)

Modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
 		[IMG]http://www.ubuntuforums.org/images/misc/progress.gif[/IMG] 	 		 		 		 		 		 	 		 			 			 				 				[[IMG]http://www.ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://www.ubuntuforums.org/editpost.php?do=editpost&p=1300648")

---


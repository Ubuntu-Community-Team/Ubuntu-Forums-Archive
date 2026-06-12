---
title: "CHanged something and lost..."
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Typo on 2006-07-17
I am using gnome and where it says applications *top left* it used to have a section which said "add/remove programs" I have kinda lost this? How can I re activate? I know I can add/remove programs in the SYnaptic tool but I want that "add/remove in my app nav.

Cheers,

---

### Post by T700 on 2006-07-17
Open the menu, right click anywhere, select Edit Menu.  Check to see if Add/Remove is unticked.  If so, tick the box, save your changes, and see if that fixes it.

Paul

---

### Post by Typo on 2006-07-17
Tried, theres nothing there that says add/remove :/

---

### Post by crossedout on 2006-07-17
Did you happen to change permissions recently on the user ID in question?  Also, if you changed administrator permissions in one ID, then it may have removed your admin privelages from the other IDs.  First check to see if you can access users permissions, System --> Administration --> Users and Groups.

If you cannot access Users and Groups:
Look in your /etc/group file and make sure your username is listed in admin.
admin:X:112:typo (or something similar, "typo" = "your username")

If not, you can add it there to correct the problem.

-crossedout

---

### Post by Typo on 2006-07-17
No I haven't changed permissions, I did delete some old clutter like music players and evolution mail etc.. To try and get rid of clutter.. But now my add/remove has gone?

---

### Post by crossedout on 2006-07-18
Check your /etc/group file that I referred to in my previous post.  If your username is missing from the admin:X:112:<username here>, then you will need to edit it.

To edit it, boot in recovery mode:
[PHP]nano /etc/group[/PHP]

Locate the line as noted above (usually near the bottom of the file), and add your username to the end of the line.
Example: admin:X:112:typo
Note: Your line may be slightly different; "typo" = "your username"

-crossedout

---

### Post by proctor on 2006-09-08
I have the same problem and cant access certain partitons, administrative tasks, etc

I tried to add my username in the groups, and because of the restrictions I have..I cannot add my name 

> "The file "/etc/group" is read-only."

"Could not save file"
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.


What can I do, also tried alt-f2 and I am the only user on here. I think this happened because of my efforts to get skype working I ran this command

> sudo chown "proctor" /dev/dsp
sudo chown username /dev/dsp
sudo chmod 666 /dev/dsp
sudo usermod -Gaudio

Ran all 4 of those to get sound up & working

---


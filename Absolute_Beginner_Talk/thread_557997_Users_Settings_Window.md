---
title: "Users Settings Window"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by corncob on 2007-09-23
I just added three new users to my Feisty machine.  That went okay as far as that goes and these new users seem to be functional.  However, when I click on Properties in Users Settings nothing happens -- the window is unresponsive.  I can only close it by clicking the X in the upper right hand.  Same thing when I try to delete these new users hoping that that might undo whatever happened.  I was thinking of changing permissions or deleting them in Terminal but don't know how.

---

### Post by Nikitas350 on 2007-09-23
Try the following to delete them:
userdel -r theusername

to change the permissions edit the file /etc/group (sudo gedit /etc/group) in this file each user is part of some groups. Try add or remove the users you want to change the permission from the groups

---

### Post by corncob on 2007-09-24
Thanks, Nikitas350.  userdel -r username got me the response from userdel "unable to lock password file".  The sudo gedit /etc/group opens a blank window with nothing in it (stuff is in the file as I can open it in Nautilus but I can't save any editing).  gksu users-admin opens the same unresponsive window.  ON the one hand I'm thinking about reinstalling Feisty but on the other, it is working otherwisw and I have so much stuff on it.

---

### Post by Nikitas350 on 2007-09-25
I forgot to add the sudo to the command. Type:
"sudo userdel -r theusername" 
(where "theusername" is the user you want to delete)
Sorry for the delay....

---


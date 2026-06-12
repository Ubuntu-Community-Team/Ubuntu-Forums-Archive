---
title: "SCIM issues"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by theRightNee on 2008-01-03
i realize i've been posting an awful lot, but i just keep running into so many obstacles :mad: 
this time, its the SCIM input setup. I cannot seem to trigger it. I have dowloaded the needed packages, and edited the file according to the guide ([https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)) i couldn't find any of the files that should have  been deleted, so that may be an issue. much thanks!:KS

---

### Post by theRightNee on 2008-01-04
bump

---

### Post by theRightNee on 2008-01-05
bump again?

---

### Post by seshomaru samma on 2008-01-05
Are you using KDE or Gnome or XFCE
Do you have Scim working in gedit (or kate in KDE, mousepad in XFCE) 
open gedit , right-click anywhere and see if you have scim under 'input methods'

Are you using an English session? a CJK session?

which of the instructions in the wiki did you follow?

> i couldn't find any of the files that should have been deleted, so that may be an issue.
what do you mean by that?
the wiki doesnt mention any files to be deleted...

---

### Post by theRightNee on 2008-01-05
my apologies for not being more specific
1. i am using an english session
2. yes i have gotten the scim to work in gedit and programs that allow the right click
3.  i did not use a wiki (should have linked this earlier) but rather this instructional [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)
   it mentions deleting files to make sure that they do not affect the new config file
4. gnome
thanks!

---

### Post by seshomaru samma on 2008-01-05
mmm...i still dont understand
if you have followed the link you provided
then you should have 
1. enable language support
2. install scim-bridge
thats it
if you are using an older version of ubuntu (not gutsy) you should have 
1. enable language support
2. run the im-switch command
if all this didn't work you should have edited the ~/.scim/global file 
(there are also additional instruction for running KDE aps but I don't think you need that)

please read the link carefully
post any questions you might have

---

### Post by theRightNee on 2008-01-05
&#35874;&#35874;&#65281;
it works!

---

### Post by seshomaru samma on 2008-01-05
&#19981;&#23458;&#27683;

---


---
title: "wine and other programs for all users."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by arron on 2007-04-19
Ok got my Fiesty, and doing a clean install.  Id like it clean and simple, so i got a couple questions...

How can i install a wine program for all users to use?  Like all users to play starcraft without a ~/.wine for each user?  I would like my home folder read only by me.  I have setup a /home/apps folder to store some other programs (google earth, sancho,nwn etc) for all users to use (/home is a big drive, / is small), which brings me to my next question in a second.  I was thinking install all into /home/apps/.wine then link everyones ~/.wine to it (use /etc/skel) would this work, or is there a easier way?

and....

How can I add the icons for wine, and for the others like google earth for all users to use?

---

### Post by x64Jimbo on 2007-04-19
This might be a bit hackish, but you could have a starcraft user with a starcraft home folder, and then whenever a user wants to play a game, you have them 
su starcraft
then
wine starcraft.exe
dunno... Just a thought.

---


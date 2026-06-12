---
title: "How do I move my thunderbird and firefox profiles?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Xaviar on 2006-04-17
I have just upgraded to Breezy Badger which i have put onto a new hard drive. I want to export my profiles from thunderbird and firefox to my new drive.  I want the new system to have the same extensions as the old one.  I have successfully saved and moved my bookmarks but that is the end of my run of luck.  I know how to copy the address book for my thunderbird but what I really want to do is to copy and move the profile in total.  I assume this will give me back the old extensions (for firefox) and  my saved mail (for thunderbird) .  Is this possible?  Is there an easy way to do it?  Any advice would be appreciated.

---

### Post by Borniet on 2006-04-17
All your settings and plugins are saved in the .mozilla folder. If you copy this one to your new installation, everything should be save (make sure you first run your firefox and thunderbird, and then copy the folder). I think it'll take a reboot of your firefox before you have your plugins back, but it is possible this way. As for thunderbird: I think you need to copy the directory (the same .mozilla directory that is), and then recreate your emailaccounts in thunderbird.  Done this a few times, and sometimes that was enough. Sometimes I had to import my old thunderbird files into the new installation. (via the file->import menu).

---

### Post by jorn on 2006-04-17
Go into home directory > hidden files. Go to .mozilla > firefox. Change the xxxxx.default map with the old one. Then go to the file "profiles.ini" and change the path to the new xxxx.default folder
Hope that works.

Jorn

---


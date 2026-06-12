---
title: "[SOLVED] vlc settings"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by vamsibethapudy on 2008-02-08
i have changed settings in vlc & put too many options on.
now i dont get to open it.
i tried it from the terminal but i get a vlc skin that doesn't respond.
how can i change the settings back to normal ?
i tried synaptic to completely remove vlc &reinstalled it.
but the settings are intact.
for that matter i want to know how this can be done for other applications too.
help!!!

---

### Post by Dr Small on 2008-02-08
Try:
```
sudo apt-get remove vlc --purge
```

That should remove all of the settings files for it, and then install it again.

Dr Small

---

### Post by Thelasko on 2008-02-08
Go into your /home/*username* (replace *username* with your user name) directory and press Ctrl+H to view the hidden folders.  Delete the .vlc folder.  Start VLC. 

Remember in Ubuntu all of your program settings are stored as hidden files under your /home folder.  If you have a major problem you can always delete that folder and restart the program.  When you restart the program it will recreate that folder with the default settings.  

Only do so if you don't care about loosing your settings.

---

### Post by vamsibethapudy on 2008-02-08
i did it to no avail.
i think i put some XOSD interface for vlc previously.
if i open it from Applications tab it does nothing
but when tried in terminal itopens this XOSD interface along with two other vlc windows all of which    dont work at all.
i tried purging as u said.
restarted the computer & then installed it.
no change at all.

---

### Post by vamsibethapudy on 2008-02-08
thnks for the advice thelasko.
it works fine now.

---

### Post by nynoah on 2008-02-08
purge VLC like previously stated.   Then go into your home folder go up to "view" and hit "show hidden files".  Delete the VLC folder in there...........then reload VLC and see if that works.   Also make sure you empty your trash before you reload VLC.

---

### Post by nynoah on 2008-02-08
Also check inside here to make sure that VLC is deleted > /usr/share/vlc  if that is not deleted after the purge, delete that.  But you may need to run this as a > alt+f2 > Gksudo Nautilus command to erase that folder.

---


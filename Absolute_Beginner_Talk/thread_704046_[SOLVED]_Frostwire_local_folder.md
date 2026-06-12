---
title: "[SOLVED] Frostwire local folder?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by briml3y on 2008-02-21
I recently installed Frostwire, and when I was setting it up I wanted to create/use a folder that all users could read/write to so that all the music/files would be downloaded to some local directory. So i created a folder /home/Shared and changed permissions so that all could read/write but when I tried to use this folder for frostwire it gave me and error saying it was an invalid folder. I'm only beginning to use Linux and help would be greatly appreciated. (Using Ubuntu 7.10)

Edit: Thought this would help;
Im trying to create a folder that all users can read/write that will be a local folder for all my music files.

---

### Post by mgranet on 2008-02-22
Since your home directory is for your user, you might try creating the folder outside of /home, and then modifying permissions. You might try creating a group with all users who want to access that folder, and then give that folder group access for the group you created. As for why frostwire couldn't access a folder in your home dir, I can't say.

---

### Post by briml3y on 2008-02-22
Where else would i make the folder or where would be the best place for it. I did try making a group and giving the group privileges to the folder.

---

### Post by mgranet on 2008-02-22
Anywhere, I would imagine. Personally, I would stick it in /usr/share .

EDIT:
Did you add all of your users to the group you created? (yourself included?)

---

### Post by briml3y on 2008-02-22
Using the user/group manger i added myself and another user to the group (the only two users at this time). I'l try /usr/share

---

### Post by briml3y on 2008-02-22
As a workaround this is what I did.
For each user allow frostwire to use /home/SOMEUSER/Shared
Changed the permission of the above folder to group read/write
In home I had a /home/Shared folder that had group read/write permission
Since I only had two users I linked the /home/SOMEUSER/Shared folders in the /home/Shared folder

So I no longer need help with this problem. For now.  :P

---

### Post by mgranet on 2008-02-22
Glad to see you figured it out! :) Make sure you mark the thread as solved.

---


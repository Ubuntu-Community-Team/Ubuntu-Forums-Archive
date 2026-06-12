---
title: "Sound Only with Main User"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by JaceMan on 2006-10-20
I just completed an install of Kubuntu.  I created user accounts for my wife and brother, after I set the system up for me.  When I log in, sound works properly, but when either of them log in, they have no sound, and kmixer has an X over it and complains 'Mixer cannot be found.'

Is this common?  What's the easiest/quickest way to get their accounts to recognize the sound card that my account obviously sees?

Thanks in advance.

---

### Post by IYY on 2006-10-21
As root, edit the file /etc/group and add their usernames to the group 'audio'.

In more detail:

sudo nano /etc/group

find the line 'audio:x:29:ilya' (just an example. my username is ilya) and modify that line to include the other users. For example, 'audio:x:29:ilya,alex' would be me and my brother.

---

### Post by aysiu on 2006-10-21
Can't you just do ```
sudo adduser *seconduser* audio
```? Substitute the second user's actual username for *seconduser*.

---


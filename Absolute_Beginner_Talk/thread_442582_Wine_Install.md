---
title: "Wine Install"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-13
I feel so noob saying this. Where is my wine installation? I loaded it up and installed Steam with it but I can't find the folders so I can put the theme in there so I can read things on steam!? Where is the Wine install?

---

### Post by Happy_Man on 2007-05-13
they are in /home/<username>/.wine/drive_c. Remember to show hidden folders by pressing ctrl+h before looking for it though.... ;)

---

### Post by TheAberrant on 2007-05-13
I'm relatively new, but I'll give this a shot.

The windows applications install in ~/.wine/drive_c/...  Where ~ is your Home directory, and drive_c is the C:\ drive as a normal windows would have.  Your programs would be under C:\Program Files\, so if you're trying to edit a config file there or read a readme, that's where I'd look.

The wine program itself installs in the /usr/bin folder, tho that may just be a symbolic link.  This is kind of speculative, but I believe that /usr/ is where most of the user installed applications go.

Hope this helped, and if I'm wrong please someone correct me :)

---


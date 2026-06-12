---
title: "[SOLVED] USB mounts but no desktop icon"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by 71CH on 2008-04-02
Hi all
I did a search on this but couldn't find an answer that helped.  I'm currently running Gutsy and everytime I plug in an external harddrive or flash drive an icon does not show up on the desktop.  The drive mounts just fine but no icon.  I looked in gconf-editor and the option is checked.  A little help please.

---

### Post by blazercist on 2008-04-02
gconf-editor

apps/nautilus/desktop/

check volumes_visible



Also, if you are using gnome and have conky running it will sometimes hide desktop icons entirely

---

### Post by 71CH on 2008-04-02
Thanks for your reply
Like I said I checked gconf-editor and its all good there
And I'm not running conky

---

### Post by blazercist on 2008-04-02
weird, do you have a Desktop folder in your /home/user/ directory?

---

### Post by 71CH on 2008-04-02
sure do

---

### Post by blazercist on 2008-04-02
sorry buddy im stumped

---

### Post by 71CH on 2008-04-02
thanks anyway
it's weird cuz it was working before and now it doesn't work anymore

---

### Post by 71CH on 2008-04-02
Ok this is gonna sound weird
On a whim I did killall gnome panel in terminal and I briefly saw the mounted usb drive icon appear towards the bottom of the desktop.  It was cut in half so it seemed like it was off the screen in a sense.  I tried to drag it up and also did the cube thing to see if I could at least see it but to no avail.  Bottom line I think the icon is there but its off the screen.  Is there anyway to select it (I'm assuming CTRL+A should do it) and drag it up without being able to click on it?

---

### Post by 71CH on 2008-04-02
Bump Bump Bump

---

### Post by annda on 2008-04-02
just an idea: first change your screen resolution to lower and then mount the disk. the icon should be placed on the visible desktop. if it is, unmount the drive again and switch back to normal resolution - the icon position should be stored

i just tested it and it works for me. if the icon **really is** off-screen as you suppose, this should fix the issue.

---

### Post by 71CH on 2008-04-02
> **annda said:**
> just an idea: first change your screen resolution to lower and then mount the disk. the icon should be placed on the visible desktop. if it is, unmount the drive again and switch back to normal resolution - the icon position should be stored

i just tested it and it works for me. if the icon **really is** off-screen as you suppose, this should fix the issue.

It worked!!!
Thank you very much :)

---


---
title: "Mounted Partition has renamed itself weird"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by bvone21 on 2007-03-26
Okay, I am a complete beginner but I do like what I've seen so far with my experiences in Ubuntu.  One odd thing that has happened though is that one of my drives that's mounted and titled "Share" has been renamed something weird ("_PNG").  Yet it's path is still "/media/share/"

I'm assuming something is just screwed up and re-mounting it (is that a word?) will make it look right.  Here's a screenshot so you can see what I'm talking about.  Everything is still functional it just doesn't display it right.

Link to screenshot:
[http://people.clemson.edu/~bschiav/screenshot.png]("http://people.clemson.edu/~bschiav/screenshot.png")

---

### Post by bulldog on 2007-03-26
Maybe you should log out and in again to see if it's fixed.

If not,right click the icon and choose rename.

---

### Post by bvone21 on 2007-03-27
I have restarted numerous times.  "rename" is grayed out when I right-click.

---

### Post by bvone21 on 2007-03-27
I have restarted numerous times.  "rename" is grayed out when I right-click.

It's name is still "share", like when i type a path to that drive I still have to use /media/share to get to it, it's just that it's displaying like that on the desktop and when I'm browsing the drive.

---

### Post by bulldog on 2007-03-27
When you choose properties,is there anything weird displayed?

You can disable them in the gconf-editor and enable them to see if that does anything good.
Hit ALT-F2 type gconf-editor and navigate to /apps/nautilus/desktop and disable the display volumes.
Log out and in and do the same except enable them to see if this works.

---


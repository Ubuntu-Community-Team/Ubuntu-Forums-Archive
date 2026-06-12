---
title: "[SOLVED] Random Screensaver List"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by NateMan on 2007-12-21
I was wondering if there was a way to edit the list of random screensavers. I have an issue with one screensaver causing a lockup of my system. In addition to that there are 3 that I would just like to get rid of. any help would be greatly appreciated!

---

### Post by Ex-windows on 2007-12-21
The One that caused similar problems 4 me and apparently many others was the "molecules" screensaver. You can delete that but i cant recal just how but inthe mean time dont use the "random" setting. You can learn more here
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/117482](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/117482). Sorry I couldn't find the fix I had used. Hope this helps

---

### Post by CatKiller on 2007-12-21
Press Alt-F2 and type **gconf-editor** into the box. Navigate to /apps/gnome-screensaver and look for the **themes** key. Remove any that you don't want from that list.

---


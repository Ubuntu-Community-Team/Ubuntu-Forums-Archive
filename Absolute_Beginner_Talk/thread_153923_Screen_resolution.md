---
title: "Screen resolution"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-04-02
I recently moved from a 15 inch monitor to a 17 inch monitor.   The current desktop resolution is 1024 x 768.  When I go to System --> Preferences --> Screen Resolution I am only offered 1024, 800, 640 or 960.  Nothing above 1024.

The video is on the mother board and under WinXP I have no problem getting 1280 x 1028, which is the native resolution for the 17-inch flatscreen I've installed.

Is it possible for Ubuntu video drivers to handle more than 1024?

---

### Post by dcstar on 2006-04-02
[QUOTE=jlhughes]I recently moved from a 15 inch monitor to a 17 inch monitor.   The current desktop resolution is 1024 x 768.  When I go to System --> Preferences --> Screen Resolution I am only offered 1024, 800, 640 or 960.  Nothing above 1024.

The video is on the mother board and under WinXP I have no problem getting 1280 x 1028, which is the native resolution for the 17-inch flatscreen I've installed.

Is it possible for Ubuntu video drivers to handle more than 1024?[/QUOTE]
Manually edit /etc/X11/xorg.conf, or:
```
sudo dpkg-reconfigure xserver-xorg
```
There are detailed HOWTOs you can find in a forum search.

---

### Post by jlhughes on 2006-04-02
Well, a search for "screen resolution" doesn't seem to help much (which I actually did try before posting).

$ sudo dpkg -reconfigure xserver-xorg

causes this message: dpkg: conflicting actions --control and --remove

This is the ABSOLUTELY BEGINNER forum and a little tolerance for less than bright questions would be helpful.

---

### Post by Gustav on 2006-04-02
it should be dpkg-reconfigure, not dpkg -reconfigure

edit:typo

---

### Post by Gustav on 2006-04-02
And for a detailed howto, look at this [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by jlhughes on 2006-04-02
[QUOTE=Gustav]it should be dpkg-reconfigure, not dpkg -reconfigure

edit:typo[/QUOTE]

Thanks. That worked.

---


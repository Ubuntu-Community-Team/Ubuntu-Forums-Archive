---
title: "Right-click with two-finger-tap+button-click does not work"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by kirillosipov on 2008-11-03
Hello everyone:

Sorry, I'm a newbie in Linux.

I have a first generation (MacBook1,1) MacBook with 2GB of memory. I have made a tripple boot setup with Mac OS, Windows XP and Ubuntu 8.04. I want to enable right-clicking the same way as it is on Windows and MacOS -- with two finger tapping. I downloaded the xorg.conf file from some of the posts (also attached here for reference). However, the problem still exists -- when I click with two finger on the touchpad, the click is still identified as a left-button click. I also monitored mouse activity with the following command:

**synclient -m 100**

So the output when I perform a two-finger-tap plus button click looks like this:

    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy 
 787.226   739  244 300 2  0  1 0 0 0 0  00000000   0  0  0   0   0
 787.326   739  244 293 2  0  0 0 0 0 0  00000000   0  0  0   0   0


So the tool "sees" that two fingers are on the touchpad. Also, the system works fine with two-finger-scrolling -- just like on Mac OS.

Can anyone advise a workaround to enable the right click?
Thanks in advance

Kirill

---

### Post by kosumi68 on 2008-11-03
[http://ubuntuforums.org/showthread.php?t=790589](http://ubuntuforums.org/showthread.php?t=790589)

---


---
title: "Bad screen resolution in Paralells mac? TRY THIS!"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-06-21
You don't need to do too much fancy stuff to xorg.conf..
All you have to do is find the list of all the resolutions where is says: "1024x756" "800x600"..
And everywhere those lists of resolutions appear, just insert your desired (and hopefully supported resolution at the front of the list.) 

So I appended 1280x800 to each list where the resolutions appeared..
such as:
"1280x800" "1024x756" "800x600"..

THEN: just run the freakin command that it tells you to (at the top of xorg.conf). IT specifically says if you ever modify this file and want the changes to be updated automatically run:

sudo dpkg-reconfigure -phigh xserver-xorg
Select vesa mode when it asks, select the screen resolution you just added when it asks..


Now, it automatically boots up when you restart x, (ctrl alt backspace), with your new resolution! I think you might have lost the ability to select anything different, but its all about the full screen mode anyways!!


NOW you dont have to go use FUSION!! Which is much slower than parallels from my experience. And the audio is handled better on parallels on a macbook too!

---


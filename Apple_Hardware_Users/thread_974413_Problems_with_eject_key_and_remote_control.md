---
title: "Problems with eject key and remote control"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by FFuser on 2008-11-07
Hi all,

I was using 8.10 development for a while and at some moment my remote control worked perfectly.
When updating my packages the remote control suddenly stopped working. (I think it was on a kernel upgrade, but I don't know for sure).

Even after a clean reinstall of 8.10 after the release the remote control didn't come back.
I did search information on the net, but nothing seemed to work (probably installing lirc will fix the problem, but since I hadn't to use that previously I wonder if that would help).

Also my eject key doesn't work (I found that installing pommed would help) but also in an earlier release that worked without any problem (without installing pommed).

Are these regressions known already, and is somebody working to resolve them?

I have a macbook 2.1

PS: I have selected [all variant] as prefix, because I think that the problem is also on other *ubuntus (I suspect it to be a kernel problem)

---

### Post by kosumi68 on 2008-11-07
1. Are you running mouseemu? If yes, uninstall it completely and restart.

2. I believe the kernel mapping was "wrong" for a while during the development of Intrepid - it is now back to what it should be. If it does not work, it could well be interference from HID - check [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) Air 1%2C1 and Intrepid work a working configuration.

3. Regarding the function keys, the reason why some keys did work before was that many function keys bypassed X. Now, gnome is supposed to take care of those keys, and so far fails on a few points. It will get better with time.

4. The eject key is not picked up by X, that is why it works to use pommed.

---

### Post by FFuser on 2008-11-07
> **kosumi68 said:**
> 1. Are you running mouseemu? If yse, uninstall it completely and restart.

This seems part of the fix (now the LEDS indicating num-lock and caps-lock are back, I didn't report it earlier that they were broken). But I loose a part of my user experience (I cant scroll anymore with my trackpad).

> 
2. I believe the kernel mapping was "wrong" for a while during the development of Intrepid - it is now back to what it should be. If it does not work, it could well be interference from HID - check [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) Air 1%2C1 and Intrepid work a working configuration.

The quirks did the trick (only I need to change 8242 to 8240)

> 
3. Regarding the function keys, the reason why some keys did work before was that many function keys bypassed X. Now, gnome is supposed to take care of those keys, and so far fails on a few points. It will get better with time.


> 
4. The eject key is not picked up by X, that is why it works to use pommed.
Remember the eject key worked in earlier version, now X doesn't pick it up anymore for some reason.


So now the sound volume keys work. But I cant use pause/next/forward (in banshee) and menu.

But when I go to the gnome shortcuts panel and select for example forward it detects my remote control key and sets the value to XF86Forward (which had worked in the past).
So it works now better but not complete yet.

---


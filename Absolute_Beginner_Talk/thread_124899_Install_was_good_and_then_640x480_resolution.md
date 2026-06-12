---
title: "Install was good and then 640x480 resolution"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by annsachd on 2006-02-02
I just installed Ubuntu on a PC with a 17" CRT monitor. Everything went fine. Then I installed Xine to watch DVDs. Worked great. 

This morning I started it up and the screen resolution is stuck at 640x480. If I try and change it, the only resolution available is 640x480. That's messed up. I checked the files and all the resolutions are there, but for some reason they aren't available.

What in the world is up with my Ubuntu?

Why would it change its resolution like that?

Why is only one resolution suddenly available in the for monitor settings?

Any help appreciated.

---

### Post by Perfect Storm on 2006-02-02
try with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by aysiu on 2006-02-02
There are only two things you need:

1. The terminal is in Applications > Accessories > Terminal
2. [This link](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) explains everything about setting up proper screen resolutions.

---

### Post by annsachd on 2006-02-03
Thanks AI, that did the trick.

I would still like someone to explain why this changed for no apparent reason.

All I had done was to install Xine to my original install.

Seems odd that it would get so funky with so little action.

---

### Post by Perfect Storm on 2006-02-03
That would be bit hard to explain, we need to see what step you made plus what you might be tickering which could have lead to changes to the xorg.conf or another reason could be there's a bug somewhere...

---

### Post by annsachd on 2006-02-03
Thanks again for the help AI. As I said, it is a fresh install with only Xine added. I guess something had changed in the rebooting process after installing Xine. I'm just glad I was able to fix it with your help otherwise I would have been condemned to viewing a 640x480 resolution which is pretty much useless.

Now on to doing all the updates for the system.

---


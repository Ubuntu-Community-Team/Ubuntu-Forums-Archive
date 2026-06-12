---
title: "Workspaces"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by jordanae on 2007-12-02
How do I get my workspaces to rotate like the ones in this video?

[http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)

And also, how do I get that box thing at the top?

---

### Post by santiagoward2000 on 2007-12-02
Hi!
The cube in the video is Beryl. However, the new project you'll want to install is Compiz-Fusion. If you are using Gusty, it should already be installed, but you'll need to configure it.
First, go to *System/Restricted Drivers Manager* and get your video card's drivers.
Then, go to *System/Synaptic*, look for **compizconfig-settings-manager** and install it. If you're using an ATI card, you should install *xserver-xgl* too to get it working.
Finally, open compizconfig and enable the **Desktop Cube** plugin. You'll probably just get 2 desktops. To fix this, go to **General Options**, and under the **Desktop Size** and set the **Horizontal Virtual Size** to 4.
That should do it.

About the bar on the top, that's Kiba-Dock. It's not on Ubuntu's repositories, but you can install it using this guide:
[http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba]("http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba")

I hope this helps! If there's any problem, just ask!
Cheers! :KS

---


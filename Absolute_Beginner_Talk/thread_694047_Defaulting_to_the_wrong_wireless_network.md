---
title: "Defaulting to the wrong wireless network?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-02-11
Hi,

I have a wireless WPA network in my house (named "swed").  I was playing with the keyrin manager & I selected a local network I can see from my house (not mine), named linksys.  

The Linksys network is unlocked & Swed is locked.  Now every reboot, the system 7.10 is defaulting to Linksys instead of swed.

How can I change this back?

Thanks,
Rich

---

### Post by spiderbatdad on 2008-02-11
To remove a wireless network from the 'preferred' list:

Hit Alt + F2 to bring up the "Run Application" dialog, then type in gconf-editor into the box. Hit Enter.

In the left pane, expand the arrows next to system > networking > wireless > networks

Select the wireless network you wish to remove.

In the right pane, right click on all lines and choose "Unset Key" from the menu that appears. (the lines should begin with something like bssids, essid, timestamp, we_cipher, etc. Once all the keys are unset, the wireless network should be removed from the list that NM will try and connect to.

From this thread:[http://ubuntuforums.org/showthread.php?p=2316847#post2316847](http://ubuntuforums.org/showthread.php?p=2316847#post2316847)


Apparently others  have struggled with this and found no other solution:[http://ubuntuforums.org/showthread.php?t=607070](http://ubuntuforums.org/showthread.php?t=607070)
[http://ubuntuforums.org/showthread.php?t=671298](http://ubuntuforums.org/showthread.php?t=671298)

---


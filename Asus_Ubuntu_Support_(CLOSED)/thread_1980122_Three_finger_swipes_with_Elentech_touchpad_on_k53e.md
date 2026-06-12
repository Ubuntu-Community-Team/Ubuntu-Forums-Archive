---
title: "Three finger swipes with Elentech touchpad on k53e"
date: 2012-05-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Helios747 on 2012-05-14
Hello,

In Windows, my Elentech touchpad detects 3 finger swipes to the right and left as browser Forward and Back commands.

I was wondering if it was possible to make that happen in Ubuntu as well. Two finger scrolling works, but it would really be the cherry on top to have that 3 finger swiping functionality.


I'm running Ubuntu 12.04 x64 with the latest updates.

Any ideas?

---

### Post by Helios747 on 2012-05-16
bumpity

---

### Post by |{urse on 2012-05-16
touchegg

[http://www.howtogeek.com/howto/43097/how-to-get-macbook-style-finger-gestures-on-ubuntu-linux/](http://www.howtogeek.com/howto/43097/how-to-get-macbook-style-finger-gestures-on-ubuntu-linux/)

---

### Post by Helios747 on 2012-05-16
That seems to be exactly what I'm looking for.

I installed it from the repos, but it kept seg faulting. A bug report said that was a known problem fixed in the SVN. I compiled from SVN, this time, it didn't crash, but multitouch gestures on my trackpad aren't being picked up by the program. I figured I'd look in the configuration file ([https://code.google.com/p/touchegg/wiki/ConfigureDevices](https://code.google.com/p/touchegg/wiki/ConfigureDevices)) but the wiki claims that Natty and higher do not need to be configured for touchpad detection. So I don't really know how to get touchegg to pick my trackpad up.

---


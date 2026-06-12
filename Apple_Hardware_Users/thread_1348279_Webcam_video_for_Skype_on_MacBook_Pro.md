---
title: "Webcam video for Skype on MacBook Pro"
date: 2009-12-07
forum: Apple Hardware Users
---

### Post by alimh on 2009-12-07
I've been searching for the past few days for a solution to my webcam video problem in Skype.

Scenario:
1. Downloaded the latest version from the Skype website.
2. Webcam (iSight) working in Cheese.
3. My buddy could see my webcam feed but I couldn't see my own (even when I went to options -> video devices and then "test") nor see my buddy.

Tried:
1. LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype - no luck.
2. Downloading the Medibuntu version of Skype - no luck.
3. 1 and 2 together - no luck.

Solution:
1. export XLIB_SKIP_ARGB_VISUALS=1 && skype (good ol' trick from the days of Beryl and Firefox)
- You should be able to use this with any version of Skype.
- You can put this line in a bash script and run the script.

Hope this helps!

---


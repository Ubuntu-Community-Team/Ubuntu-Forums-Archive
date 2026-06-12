---
title: "Workaround for too-low-res during install"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bsmith1051 on 2007-11-20
**FYI**
If you're trying to do a new install but you can't view the Install Wizard, you need to increase the resolution to at least 1024x768:

**TEMPORARILY UPDATE VIDEO DRIVER ON-THE-FLY**
1. open System > Administration > Restricted Drivers Manager
2. enable any proprietary video driver;
   If there isn't one for your video card then see final comment...
3. instead of rebooting as prompted, press CTRL-ALT-BACKSPACE to reload the video-driver system.
4. The new driver should take effect immediately and will hopefully allow you to choose 1024 or higher resolution (if it doesn't simply default to it)

**IF THERE'S NO OTHER VIDEO DRIVER LISTED**
Can you find an alternate video driver somewhere on the web?  If so, you can try the same general technique -- manually download and install the alternate driver, then manually restart the X Server (step #3).

---

### Post by master_kernel on 2007-11-20
This should be moved to Tutorials and Tips.

---


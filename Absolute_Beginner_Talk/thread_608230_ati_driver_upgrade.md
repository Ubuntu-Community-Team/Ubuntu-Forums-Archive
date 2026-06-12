---
title: "ati driver upgrade"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by mubelhor on 2007-11-09
I'm sorry, but I can't find the posts about how to upgrade the ati driver to enable a widescreen monitor, desktop effects and dual monitor support.  By dredging up what I remembered about using dr dos, I managed to get to the step of "remove any old fglrx debs from /usr/src/, which was unsuccessful, and then the "sudo mkdir / Lib/modules/$(uname -r)/volatile" step failed.

Which directory should I be in at the mkdir step?  The command seems so basic, but it keeps failing for me.

---

### Post by Pumalite on 2007-11-09
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by gn2 on 2007-11-09
Have you tried using Envy to sort your graphics driver out for you?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mubelhor on 2007-11-09
I just now tried Envy, but it just made my screen resolution worse.  I probably did something wrong.  I thought I was so close with the steps spelled out in whatever post explained how to install the recently released ati driver for linux.  Maybe my system simply isn't going to work with Ubuntu.

---

### Post by mubelhor on 2007-11-10
I got it to work!  I kept trying "Method 2" in the installation guide from cchtml.com., and finally succeeded.

---

### Post by Pumalite on 2007-11-10
Good for you!

---

### Post by mubelhor on 2007-11-10
I spoke too soon.  On reboot, I get a brief glimpse of my desktop, and then I see a light gray screen with only the mouse pointer showing.  So much time lost in this effort...

---

### Post by Pumalite on 2007-11-10
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---


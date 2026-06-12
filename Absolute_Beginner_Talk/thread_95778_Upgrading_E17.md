---
title: "Upgrading E17"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by joflow on 2005-11-27
Hi,

I used the guice found here to install enlightenment 17 from the Shadoi repo ( [http://www.ubuntuforums.org/showthread.php?t=79155&highlight=e17](http://www.ubuntuforums.org/showthread.php?t=79155&highlight=e17) )

I then used the guide found here: ( [http://www.ubuntuforums.org/showthread.php?t=54476&highlight=e17](http://www.ubuntuforums.org/showthread.php?t=54476&highlight=e17) ) to combine Gnome with Enlightenment.

The version found in the Shadoi repo is version 0.16.999.018.  I wanted to upgrade to version 0.16.999.019, so I went to enlightenment.freedesktop.org and downloaded the source for eet, evas, ecore, embryo, edje, and enlightenment.  I compiled and installed all of this with seemingly no errors.  But when I left click -> About Enlightenment...it still says 0.16.999.018 in the about window.

How do I replace 0.16.999.018 with 0.16.999.019?

---

### Post by Turtle.net on 2005-11-27
For me it's because your 0.16.999.018 is still installed (as a package) and your own compiled version 0.16.999.019 is maybe not installed properly (let say in the good folders maybe ?).
Try to found a new repository with the version 0.16.999.019 and do un upgrade.

Or you can try to uninstall 0.16.999.018 using synaptic and recompile and install your own version

Maybe this post can be useful [http://www.ubuntuforums.org/showthread.php?t=59568&highlight=enlightenment+bleeding]("http://www.ubuntuforums.org/showthread.php?t=59568&highlight=enlightenment+bleeding")

Good luck ;)

---


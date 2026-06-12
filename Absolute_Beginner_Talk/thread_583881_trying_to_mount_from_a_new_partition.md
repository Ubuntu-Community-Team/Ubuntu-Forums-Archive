---
title: "trying to mount from a new partition"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by alarichall on 2007-10-20
When I first came to ubuntu (6.10 as it happens) I just made my hard disk into one big partition, called hda1.

Then I wanted to use ubuntu 6.06, so I created another partition, called hda3, and installed ubuntu 6.06 on it. When my computer boots up, it gives me the option of booting either from this or from hda1, with hda3 as the default option. When I boot from hda3, hda1 appears on my desktop, and I access all my old files on hda1 through it.

Then I created another partition, called hda4, and copied the contents of hda3 to it using GParted.

In GParted, my hard disk now looks like this:

[IMG]http://alarichall.googlepages.com/Screenshot.png[/IMG]

What I was expecting was that when I rebooted the computer, I would now be given to option of booting from hda1, hda3 or hda4. But I'm not given that option--I just get hda1 and hda3. Can anyone help me?

Incase it's useful to know, when I boot from hda3, hda4 doesn't appear on the desktop even though hda1 does. And when I go to places > computer, it lists my CD-ROM drive, hda1, Filesystem, and a '9.8 GB Volume'. I assume that the latter must be hda4. When I right-click on it and click 'mount' it says 'unable to mount the selected volume', and when I click on 'show more details' it says 'error: device /dev/hda4 is not removable; error: could not execute pmount'.

Any assistance much appreciated. As you can see, I'm totally beginnertastic.

---


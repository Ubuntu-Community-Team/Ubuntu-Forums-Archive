---
title: "Nvidia X Server Not Saving"
date: 2012-08-16
forum: Any Other OS
---

### Post by DaimyoKirby on 2012-08-16
Hi there.
Whenever I turn my computer on, I have some flickering.  It's not so bad that I can't do anything, but it will start to give me a headache when I look at my screen for too long.
So I went into the Nvidia X Server Settings, and changed the refresh rate from 60hz to 75hz, and voilà! It stops flickering.
But then, when I turn my computer back on later, it's flickering again! And the Nvidia X Server is back to 60hz refresh, even though I saved it last time I changed it.
(I found this guy is having the exact same issue, halfway down the second paragraph:[http://toastytech.com/guis/ubuntu114.html]("http://toastytech.com/guis/ubuntu114.html"))

So my question is:
Is anyone else experiencing this problem?
Does anyone know a solution to keep the monitor/x server at the correct refresh rate?

Specs:
Dell XPS 400
Nvidia GeForce GT430
Zorin OS 6

---

### Post by BicyclerBoy on 2012-08-17
It could be the permissions on the .nvidia-settings-rc file..
This file (.hidden) is in your user home folder.
I came across this problem some time back..

nvidia-settings stores its settings in that hidden file & some/other settings into /etc/X11/xorg.conf if you save to xorg.conf.

AFAIK you **don't** want to use sudo to run nvidia-settings. If the file permissions (.nvidia-settings-rc) are okay you do not have too.

---

### Post by DaimyoKirby on 2012-08-23
Ok, sorry it was so long to get back, I've been quite busy.

Basically, I don't know what was causing it, but a new update in the version-current Nvidia drivers corrected the issue.
So this post is moot. But thanks anyway!

---


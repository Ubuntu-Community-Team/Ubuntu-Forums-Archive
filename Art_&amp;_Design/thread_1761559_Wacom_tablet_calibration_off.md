---
title: "Wacom tablet calibration off"
date: 2011-05-18
forum: Art &amp; Design
---

### Post by Triblaze on 2011-05-18
[B]PROBLEM SOLVED, MOVE ALONG.

Would lock but I'm new and don't know where the lock button is. Or even if threads get locked here...
[/B]

Well, new here, been lurking this place ever since I got Ubuntu but never bothered to get an account until now, because I'm getting a bit tired of searching for some stuff and figure sometimes it's better to just ask.

Any ways, got a Wacom Bamboo Pen a few days ago, sudo apt-get'ed Waom dkms, plugged it in, it worked perfectly out of the box, pressure and everything.  However, my little sister liked playing around on it, so I decided to set it up for my mom's computer, since that's the one my sister uses (windows). So, I put it in, install the drivers, it works perfectly.

But now when I take it back to my computer and plug it in, the calibration is way off, it moves around the screen only if I'm at the very left of the tablet, and is very jumpy, likely due to the narrow space on the tablet that covers the whole range of screen movement.   So, how do I fix it? Read some stuff about the Xorg.conf file, but I never had to mess with it to set this up and I don't know exactly what I'd need to do for this sort of calibration/resetting what the tablet detects as the screen size, so I came here.   Any thoughts?

---

### Post by robert shearer on 2011-05-18
This thread is what you want...
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

First page how-to covers it all. :)

If you get stuck post there and help will be at hand.

---

### Post by Triblaze on 2011-05-18
Thanks!


I think I found the problem, the MaxY value should be 92000, but my Xorg.0.log says it's at 9200, one zero short, which would explain why only the very left is mapped to the screen.

Edit: Wait...maybe it's that some X's are set to -2147483648. I don't know...

Now how to fix...
Where do I change that?

---


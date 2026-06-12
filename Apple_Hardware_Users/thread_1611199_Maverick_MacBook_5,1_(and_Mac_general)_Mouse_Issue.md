---
title: "Maverick: MacBook 5,1 (and Mac general): Mouse Issues"
date: 2010-11-01
forum: Apple Hardware Users
---

### Post by CalaverX11 on 2010-11-01
I've seen many (unanswered) threads about this, so I'm asking again, specifically relating to Maverick on a MacBook 5,1 (and probably others) regarding the following:

 - Touchpad sensitivity
Horizontal tracking across multiple displays is 2-3x faster than vertical tracking. Note that vertical tracking stays the same regardless of multi-monitor orientation; horizontal tracking seems to be the only thing affected by multi-monitor placement. This problem does not exist in single-monitor mode--x and y tracking is 1:1. There are no GUIs, xinput or other parameters I can find to adjust the x tracking resolution in multi-monitor mode, unless I'm just missing something. At this point I've tweaked every available parameter in xinput to see what they did, and none of them affected only the x resolution the way I would like.

 - Magic Mouse scrolling
I have found several unanswered threads about this problem. Magic Mouse scrolling is terrible, and can't be adjusted using any of the GUIs available, nor by xinput. The ONLY existing solution is exclusive to Firefox. As above, I tried every xinput parameter for the driver available and could not get the scroll tracking to adjust at all. It's still static, at roughly 3-5 "lines" per tick, and the tick resolution is too great (my finger slides nearly the entire length of the mouse for only three or four ticks).

I am willing to look at source and compile new drivers if someone can point me in the right direction. Google is useless here, as the top 100 or so results all refer to the same handful of threads here on this forum, all of which remain unanswered to this day. If anybody out there has any new information regarding these problems, I'd love to hear about it, even if it's tucked away in some obscure blog nobody reads (which is why it wouldn't show up in the first dozen pages of Google results).

---

### Post by Old Codger on 2010-11-01
Calaver X11,

Thank you for posting. I've been wondering about some of these issues, too. For example, numerous folks have posted about wireless keyboard (iMac)and mouse problems on various Macs, but so far, I haven't seen fixes.:(

OC

---

### Post by CalaverX11 on 2010-11-01
> **Old Codger said:**
> Calaver X11,

Thank you for posting. I've been wondering about some of these issues, too. For example, numerous folks have posted about wireless keyboard (iMac)and mouse problems on various Macs, but so far, I haven't seen fixes.:(

OC
I haven't tried my BT keyboard under Linux yet, but I haven't had any other issues not mouse-related. Overall, Maverick's support for MacBooks with the Mactel drivers is outstanding. I just wish these two little tweaks were possible.

---


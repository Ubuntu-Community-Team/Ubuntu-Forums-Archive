---
title: "monitor not recognized : iiyama prolite e2207ws"
date: 2011-10-18
forum: Any Other OS
---

### Post by gruadp on 2011-10-18
I have a dual-monitor-configuration (one BenQ and one iiyama-widescreen).  On old Ubuntu 11.04 both monitors where somehow recognized. At least I could select a widescreen-resolution for my iiyama.

Now - after a fresh install - I can select only 1024x768 or 800x600 for the iiyama-monitor which is detected as "unknown"

any way to tell my new ubuntu 11.10 about my iiyama-monitor or at least make it offer more generous resolutions including widescreen-resolutions??

I looked in /etc/X11 but xorg.conf seems to be gone and I'm not missing it. It always confused me big time.

thnx

---

### Post by Gremlinzzz on 2011-10-18
SAME here single monitor :popcorn:

Think it has something to do with the new kernels.
cause i switched to linux mint still the same.

---

### Post by gruadp on 2011-10-20
solved:

after I installed the fglrx-drivers for my graphiccard  (I have an ATI-card and I had to install the drivers manually cause ubuntu-restricted-drivers jockey-backend seems utterly broken) the monitor was finally recognized within the ati catalyst center (specific to my driver, comes with the driver) and ubuntu display-settings.

hope this is true for other graphiccards as well.

---


---
title: "help with wpa_gui?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by eljalill on 2007-10-04
hello,
I please need help with getting wpa_gui up and running. I need it for connecting to my university network, they use 802.1x.

I made sure that wpa_supplicant runs in the background (with -Bw as options), but still when I am trying to run wpa_gui (as me or with gksu) I get an error message:

Failed to open control connection to wpa_supplicant

I have a Intel Corporation PRO/Wireless 2200BG, and it worked fine so far (with wicd).

I am really thankful for any help/suggestions! I've read around on the forums, but I couldn't find the answer to this...

---

### Post by sfenton on 2007-12-19
This is because you don't have this in your wpa_supplicant.conf file

ctrl_interface=/var/run/wpa_supplicant

You will also need to run wpa_gui with sudo. 

I've been racking my head for about a hour on this, and then understood the error message sort of. I also noticed in the man pages that wap_gui is looking in /var/run for wpa_supplicant. 

HTH.

---


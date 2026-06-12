---
title: "Configuration Editor"
date: 2006-12-18
forum: Apple PPC Users
---

### Post by andrewlondonuk on 2006-12-18
I've finally managed to get Ubuntu to install on my imac g3 and have a couple of quetions.

Firstly, how do i go about installing the configuration editor that should be in the system tools menu? I'd like to enable icons on my gnome desktop so need this. Secondly, i've got mp3s working, it's just that even with the sound turned all the way up it's still quite quiet. Does anyone have any ideas how to fix this?

Thanks,
Andrew

---

### Post by renzokuken on 2006-12-18
for the sound issue, type **alsamixer** in the terminal, and check that all relevant options are unmuted. or just play with it till the sound is at a suitable level

---

### Post by Peter76 on 2006-12-18
For the sound issue; at least under Edgy the sound module doesn't get loaded:

sudo modprobe snd-powermac

If this gets it working add it to /etc/modules to get it working after you reboot.

To get the gconf-editor in your menu, open up the menu-edotor and add it through there

Good luck

---


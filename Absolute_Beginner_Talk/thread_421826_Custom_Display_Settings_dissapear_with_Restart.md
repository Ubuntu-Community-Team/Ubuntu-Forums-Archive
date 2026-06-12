---
title: "Custom Display Settings dissapear with Restart"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-24
I tried to change the resolution of my screen to 1280x800 using the "NVIDIA X Server Settings" under System Tools. However, if I restart my computer, the resolution goes back down to 1024x768. How do I make sure that the computer will always start with the higher resolution settings?

---

### Post by johnny4north on 2007-04-24
does your videocard and monitor support this res and do be very careful.  wrong res and refresh rate can damage monitor.  read the read me at the nvidia web site. its right next to the linux drivers. [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)  each read me is specific for the driver.  you may need to edit your xorg.conf file be very careful in there.  back up everything  1st.

---

### Post by joshaude on 2007-04-25
I had the same problem and I know for sure that my hardware can support the resolution.

---

### Post by Nythain on 2007-04-25
nvidia settings cant write the changes to xorg.conf unless you run it with sudo... so all the changes you make are temporary till you run sudo nvidia-settings or whatever, make the changes, and tell it to save changes to xorg.conf

---


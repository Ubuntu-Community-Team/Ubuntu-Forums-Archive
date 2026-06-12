---
title: "Conflict with using Touch Pad and nvidia-settings"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-05-29
I installed the Touch Pad utility using the Add/Remove. When I tried to run it I got the error message saying that I need to set "SHMConfig" "true" in xorg.conf under the Synaptics section. However, when I went to check it it was not there. I then checked the xorg.conf.backup which was created when I installed the NVIDIA driver from [www.nividia.com](www.nividia.com) and it was there. I also realized that when I used "nvidia-settings" to change display settings and saved it to the xorg.conf file, it would overwrite it. How can I get the original xorg.conf file to use the Synaptics section but still keep settings from the nvidia-settings? Mainly its the resolution that I want. With nvidia-settings, I set it to Auto which always stays at 1280x800.
__________________

---


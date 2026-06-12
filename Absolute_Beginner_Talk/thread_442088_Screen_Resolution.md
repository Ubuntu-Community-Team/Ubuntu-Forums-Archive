---
title: "Screen Resolution"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by hangdogdaddy38 on 2007-05-13
Every day i have to reset my resolution back to 1360 by 768. I don't understand why it keeps going back to the 1024 by 768. Configuration says: Separate X screen. Any help will do. Thanks, mike.

---

### Post by Wiebelhaus on 2007-05-13
Open terminal

Type
> sudo nautilus

Locate
> /etc/X11/xorg.conf

Create backup of xorg.conf (Copy the file then re-paste & re-name
> xorg.conf.backup

Open xorg.conf paste this in the exact location that the sub section display is , over writing the original display subsection.
> SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

if you need 1400x900 add it , save - restart - set resolution.

Print this just in case it blows up
[http://ubuntuforums.org/showthread.php?t=258186&highlight=restore+xorg](http://ubuntuforums.org/showthread.php?t=258186&highlight=restore+xorg)

---


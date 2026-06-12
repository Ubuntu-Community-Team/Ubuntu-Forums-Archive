---
title: "Refresh/resolution wrong in terminal - OK in Gnome"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Iowan on 2006-10-30
Under Edgy, after the original splash, there's a brief moment when the screen seems to lose sync., but then the Desktop appears.  If I CTRL-ALT-F1 (through  CTRL-ALT-F6), it loses sync.
Computer is Dell Optiplex GX110
**xorg.conf **contains```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82810E DC-133 CGC [Chipset Graphics C
ontroller]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

---

### Post by Iowan on 2006-12-07
[http://ubuntuforums.org/showthread.php?t=298678]("http://ubuntuforums.org/showthread.php?t=298678")
Who'd have thought it could be as simple as deleting **splash** from the **kernel** line in **/boot/grub/menu.lst**

---

### Post by drFUNK on 2006-12-20
Very strange.  The exact same thing happened to me - the same fix worked too.  Seems like an issue with that intel card.

---


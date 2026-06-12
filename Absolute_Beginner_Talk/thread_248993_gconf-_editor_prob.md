---
title: "gconf- editor prob"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by SoftTaco on 2006-09-01
I am trying to set my screen resolution to 1280x1024 and the highest i am offered is 1024x768.

i did dpkg-reconfig xserver-xorg
i added "1280x1024 to xorg.conf
but when i go into gconf-editor,
"/desktop/gnome/screen" is missing

any ideas?

---

### Post by orb9220 on 2006-09-01
You don't fo to gconf-editor to set resolutions system>perferences>screen resolution.

---

### Post by SoftTaco on 2006-09-01
right but my desired resolution is not available in there

---

### Post by SoftTaco on 2006-09-02
alright so assuming i am completely off bese with the whole gconf-editor thing. How do i get my gnome preferences to have more screen resolutions available?

ive done dpkg-reconfig xserver-xorg and added the resolution i wanted there: no change

i thought i got it into xorg.conf right but just incase:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Trident Microsystems CyberBlade XPAi1"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

```

where do i go from here?

---


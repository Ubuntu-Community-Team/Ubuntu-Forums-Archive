---
title: "[PPC] Low-end video? Try 16-bit default depth"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by stream303 on 2008-05-08
Ordinarily something like this belongs in another forum, but since many ppc'ers may be running low-end video, this is a simple reminder and how-to especially for new Hardy users.

Unless you plan to edit photos, or something else that needs all those colors, you can gain some video speed by dropping your default depth from 24 down to 16.  I'll use Hardy's xorg.conf snippet as an example:

To edit:
```
sudo nano -w /etc/X11/xorg.conf
```

At the screen section, force a lower default-depth:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        **DefaultDepth 16**
EndSection
```

Save the file.
Now just logout and login again.  You can check your /var/log/Xorg.0.log file for a line something similar to this:

```
(**) NV(0): Depth 16, (--) framebuffer bpp 16
```

Aside from this, there are also the good tips for some ppc tweaks for ati cards here:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

---


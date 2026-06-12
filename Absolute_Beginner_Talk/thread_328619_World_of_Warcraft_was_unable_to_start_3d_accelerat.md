---
title: "World of Warcraft was unable to start 3d acceleration"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-12-31
Si installed WoW under wine using this guide: [http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft)

now when i run WoW i get this error message:
World of Warcraft was unable to start 3d acceleration

ive got an ati card and am running an old version of compiz...

Any help would be great thanks.


when i run WoW from the comand line i get these errors:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3eee0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f688,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f674,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f688,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f674,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f688,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f674,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f688,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fd3f674,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x2c), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x2c!


maybe wine cant find the fglrx drivers?

---

### Post by pissedoffdude on 2006-12-31
> **jinxjinx said:**
> Si installed WoW under wine using this guide: [http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft)

now when i run WoW i get this error message:
World of Warcraft was unable to start 3d acceleration

ive got an ati card and am running an old version of compiz...

Any help would be great thanks.

try disabling compiz

---

### Post by jinxjinx on 2006-12-31
so i typed metacity --replace to switch window managers but still no luck....

---

### Post by Sammi on 2007-01-01
Try updating or even uninstalling Compiz. Beryl may also be a viable option.

Anyway there is a community maintained Ubuntu specific WoW/Wine howto: [http://help.ubuntu.com/community/WorldofWarcraft](http://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by jinxjinx on 2007-01-02
thanks for the responce. i cant seem to find the WoW/wine forum. 

also when i try with other window managers i get the exact same error

---

### Post by Sammi on 2007-01-02
Sry the link was borked. It's fixed now.

---


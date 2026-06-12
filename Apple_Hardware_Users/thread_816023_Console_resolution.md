---
title: "Console resolution"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by mariguango on 2008-06-02
How i may set up my console and boot resolution to my native 1680x1050? On macbook pro with ati x1600.
I try to use startupmanager, but it don't let me use my own resolution.

---

### Post by cyberdork33 on 2008-06-02
> **mariguango said:**
> How i may set up my console and boot resolution to my native 1680x1050? On macbook pro with ati x1600.
I try to use startupmanager, but it don't let me use my own resolution.
I don't think you can use 16:9 resolutions at the console (and maybe the bootsplash too) since these rely on framebuffer/VESA modes. There is a section (#6) here on setting the console resolutions.
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Be careful as for some reason, many modes don't work for me on my iMac (w/ X1600 as well). if you get an unusable display, you can edit the kernel line in grub by hitting 'e' to remove the vga statement.

---

### Post by mariguango on 2008-06-03
> **cyberdork33 said:**
> I don't think you can use 16:9 resolutions at the console (and maybe the bootsplash too) since these rely on framebuffer/VESA modes.

Yes, i hear about it, but i hope that should be solution )

---

### Post by cyberdork33 on 2008-06-03
> **mariguango said:**
> Yes, i hear about it, but i hope that should be solution )

None that I know of. I think it will be dependant on VESA supporting other modes, which is not really a priority issue since "looking good" is not a functional requirement.

---

### Post by mariguango on 2008-06-03
> **cyberdork33 said:**
> None that I know of. I think it will be dependant on VESA supporting other modes, which is not really a priority issue since "looking good" is not a functional requirement.

yes, but on lcd panels little fonts looks more clear with native resolution, i understand that it not primarly needed function, but i want perfect stuff on my computer :)

and i hear that not only vesa may be used here, but also patched vesa, radeonfb and may be more ways. I ask here for someone who may know this, cause it easy then finding solution by myself.

Thank you once again.

---

### Post by robertyou on 2008-11-20
I know that startupmanager in the depository should do the trick, but think it only has a fixed set of resolution to choose from.(In your case, 1600x1200 is the closest)

---


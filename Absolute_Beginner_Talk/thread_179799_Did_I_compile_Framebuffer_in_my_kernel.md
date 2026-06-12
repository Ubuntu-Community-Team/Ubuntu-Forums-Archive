---
title: "Did I compile Framebuffer in my kernel?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Resurrection on 2006-05-20
I used search and while there are many threads on framebuffer support, I am not sure if I compiled it in properly with my custom kernel.

I compiled the vanilla 2.6.16 kernel with the ck10 patch.  I have upower installed for an older kernel with my nvidia GeForce 5500 FX (256 mB) card, and it works fine, so my system is set up driver wise properly.  I am having some issues getting it to work with my new kernel, as in after grub, I don't get any kind of splash at all, not even verbose.  Not until Gnome starts.

So I am thinking that I didn't compile framebuffer support properly into my new kernel, so below is a chunk from my /usr/src/linux/.config file.  

> #
# Graphics support
#
CONFIG_FB=y
CONFIG_FB_CFB_FILLRECT=m
CONFIG_FB_CFB_COPYAREA=m
CONFIG_FB_CFB_IMAGEBLIT=m
# CONFIG_FB_MACMODES is not set
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y
CONFIG_FB_CIRRUS=m
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
CONFIG_FB_CYBER2000=m
# CONFIG_FB_ARC is not set
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
CONFIG_FB_VGA16=m
# CONFIG_FB_VESA is not set
CONFIG_VIDEO_SELECT=y
CONFIG_FB_HGA=m
CONFIG_FB_S1D13XXX=m
CONFIG_FB_NVIDIA=m
CONFIG_FB_NVIDIA_I2C=y
CONFIG_FB_RIVA=m
CONFIG_FB_RIVA_I2C=y
CONFIG_FB_RIVA_DEBUG=y
CONFIG_FB_MATROX=m
CONFIG_FB_MATROX_MILLENIUM=y
CONFIG_FB_MATROX_MYSTIQUE=y
CONFIG_FB_MATROX_G=y
CONFIG_FB_MATROX_I2C=m
CONFIG_FB_MATROX_MAVEN=m
CONFIG_FB_MATROX_MULTIHEAD=y
# CONFIG_FB_RADEON_OLD is not set
# CONFIG_FB_RADEON is not set
# CONFIG_FB_ATY128 is not set
# CONFIG_FB_ATY is not set
CONFIG_FB_SIS=m
CONFIG_FB_SIS_300=y
CONFIG_FB_SIS_315=y
CONFIG_FB_NEOMAGIC=m
CONFIG_FB_KYRO=m
# CONFIG_FB_3DFX is not set
# CONFIG_FB_VOODOO1 is not set
# CONFIG_FB_CYBLA is not set
CONFIG_FB_TRIDENT=m
CONFIG_FB_VIRTUAL=m

#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=m
# CONFIG_FRAMEBUFFER_CONSOLE_ROTATION is not set
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y

Based on the above, due I have framebuffer compiled in properly?  Note:  I am not really concerned about the upower splash not working, as I am enjoying "getting my hands dirty" and tweaking it on my other kernel.  This is really for me to learn more about the options you choose at compile time.

---

### Post by Ptero-4 on 2006-05-20
You have the framebuffer set up right. What's missing there is the VESA framebuffer driver, not a showstopper if the nvidia framebuffer supports your videocard model. But if it doesn't you'll need to recompile the kernel and ensure that VESA framebuffer support is compiled.

---

### Post by Resurrection on 2006-05-20
ok, I will go back in and do a recompile, :-D while I have some time to kill.  This time I will enable VESA framebuffer and see what happens, plus it gives me a chance to remove some other stuff that I now know I don't need.

---


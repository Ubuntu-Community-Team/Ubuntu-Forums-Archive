---
title: "Install problem Dell Latitude C800"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by dstew on 2007-04-02
I am hoping to install Ubuntu either 6.06 or 6.10 on Dell Latitude C800 laptop, with an ATI M4 video controller. I ran the GParted Live CD, and its screen looked funny (split into sections) so I tried it in the Force VESA mode, and I got a small but workable display. I shrunk the Windows XP FAT32 partition down, and made a 10Gb ext3 partition and a 1 Gb swap partition for the Linux install. Windows still boots fine, so now I am ready to install Ubuntu.

However, when I boot the 6.10 live Cd, the screen turns white, and I can't see anything. This live CD works fine in other computers, and I have used it to install before. I then tried alternative install CDs for 6.06 and 6.1, but I get the same thing -- white screen. Any ideas?

---

### Post by justin whitaker on 2007-04-02
You could try passing a boot parameter to the system.

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-parms.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/boot-parms.html)

In particular:

>  debian-installer/framebuffer

    Some architectures use the kernel framebuffer to offer installation in a number of languages. If framebuffer causes a problem on your system you can disable the feature by the parameter debian-installer/framebuffer=false, or fb=false for short. Problem symptoms are error messages about bterm or bogl, a blank screen, or a freeze within a few minutes after starting the install.

    The video=vga16:off argument may also be used to disable the kernel's use of the framebuffer. Such problems have been reported on a Dell Inspiron with Mobile Radeon card.


Good luck!

---

### Post by dstew on 2007-04-02
Thanks for answering. I was going to try to make some changes at the splash screen, even though I could not see it, by practicing on a system where I could see the screen, and entering keystrokes "blind". I was going for the simplified graphics install, but before I got to enter my memorized key strokes, the screen appeared! Now I can see the menu. I didn't do anything, but after about the 10th time trying to boot the same disk, it worked. Maybe there was some dust in the CD drive or something. Anyway, your post brought me luck. Thanks.

EDIT: Next boot failed again. Looked at BIOS settings again. Changed Boot Speed from **default** (1GHz) to **compatible**. Now it boots fine.

---


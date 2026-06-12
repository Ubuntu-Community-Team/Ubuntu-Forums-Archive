---
title: "Video Signal Out of Range"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2007-05-18
When I boot Ubunty 7.04 there is no splash screen and my monitor displays "video signal out of range" instead.  I know that I can override the default video signal by adding something like vga=792 in the menu.lst file.  But 792 doesn't work for my ViewSonic LCD monitor.  Where can I find a list of all the possible values?  

Thanks,
Don

---

### Post by n8bounds on 2007-05-18
you sound like you know how to edit grub fine, so try 

vga=ask


notes:
vga= mode

    Specifies the VGA text mode that should be selected when booting. mode defaults to the VGA mode setting in the kernel image. The values are not case-sensitive. They are:


    ask

        Prompts the user for the text mode. Pressing Enter in response to the prompt displays a list of the available modes.

    extended (or ext)

        Selects 80x50 text mode.

    normal

        Selects normal 80x25 text mode.

    number

        Uses the text mode that corresponds to number. A list of available modes for your video card can be obtained by booting with vga=ask and pressing Enter.

---

### Post by mengd2002 on 2007-05-18
It works.  You have to remove the "quiet splash" option from the kernel line.  But that's OK because I can see the boot messages instead of the splash screen.

---

### Post by n8bounds on 2007-05-19
awesome

---


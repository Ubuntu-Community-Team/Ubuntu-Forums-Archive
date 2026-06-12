---
title: "Error while booting Gutsy"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2008-02-03
What does this mean?
> [   24.237959] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
That's what I get every time I boot up. It continues to boot and operate normally except for some stuff that doesn't work.

What is this PCI thingy?

Thanks,
Eric

---

### Post by spiderbatdad on 2008-02-04
you may have a config setting in your bios for pci. Or it may work for you to edit /boot/grub/menu.lst (small "L") ```
gksudo gedit /boot/grub/menu.lst
``` this will open a graphical text editor with super user privileges. Scroll down till you see something like ####END DEFAULT OPTIONS####
Now you will see LInux boot options. In the first block of text with your version, etc, go to the end of the line that starts with the word Kernel. Delete the words ro --quiet splash, and add "noapic nolapic vga=792" without quotes. Save the file and reboot. Let me know if this worked

---

### Post by nowhere@cox.net on 2008-02-04
Thanks for the info. I haven't tried it yet. I was wondering what functionality I will loose by disabling apci like tihs? I have a sidebar screenlet running on my desktop with temperature settings and such on it. Also, I use the built-in function keys like for volume and wifi and such. Only ones that don't work are the screen brightness. The OSD pops up and the slider moves but the brightness stays the same.

Thanks,
Eric

---


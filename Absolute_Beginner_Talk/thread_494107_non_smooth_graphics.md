---
title: "non smooth graphics"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by usholti on 2007-07-06
I know that similar problems are already discussed but I'm not able to solve it! Or perhaps I missed something!

I have installed Ubuntu on a desktop computer. 
Everything works fine but graphics!

When I drag a window or trying to scroll its content the movement is not smooth. Actually the behavior is very annoying. I've tried to reconfigure the X Window System configuration file (xorg.conf) using the suggested command and specifying the correct (?) driver, but it has been necessary to recover the previous configuration.

Here is what I know about the graphic controller (obtained using lshw):

           *-display
                description: VGA compatible controller
                product: UniChrome Pro IGP
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f4000000-f7ffffff iomemory:fb000000-fbffffff irq:5

Note: I do not know how to identify more exactly the card.

Thanks for your help.

---

### Post by DBStevens on 2007-07-06
If you could provide the following:

dmesg

and

cat /proc/mttr

and 

cat /var/log/Xorg.0.log

and

sudo lspci -v


I'll take a stab at it.

---

### Post by usholti on 2007-07-11
Sorry for this late answer. The machine was unavailable for a while...
I have attached the required informations.

---

### Post by DBStevens on 2007-07-11
You are using the generic vesa driver, you should switch to the proper VIA supported open source drivers.  It should provide a major improvement in graphics handling.

I also have not been able to account for the complexity in your mtrr setup, I get concerned when I can't locate all of the address ranges, however I don't see any glaring issue there (there are too many hands in the mtrr setup process).

You didn't say what was turned on for graphic effects or the actual windows manager in use.

I'd visit the VIA web site and get the correct driver and install it.

Good luck.

---

### Post by ev5unleash1 on 2007-07-11
Yes, it looks like when Ubuntu was installed it thought your video driver was VGA or did not know what it was so used that one. It's not the one for your current driver. So try to find the right drivers for your video card.

---

### Post by regomodo on 2007-07-11
i'm fairly sure you need to set the default video bit depth from 24 to 16bit. It makes gradients a lot smoother along with allowing you to scroll and move boxes above fine. 

Not all comp's need this but my laptop does. What is the computer?

To do the above open up terminal and enter

gksudo gedit /etc/X11/xorg.conf

Enter your password and look in the file for the words "default bit depth", or something like that. It'll have the number 24 beside it. replace that with 16 and save the file.

Exit the file and press ctrl+alt+backspace. That'll restart your xsession. Hopefully that will sort things as long you touch nothing else

---


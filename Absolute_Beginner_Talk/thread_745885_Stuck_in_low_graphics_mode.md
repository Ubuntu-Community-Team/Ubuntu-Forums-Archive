---
title: "Stuck in low graphics mode"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Essel on 2008-04-05
So, I've looked at the other topics on this subject, and none seem to fix my problem.
Yes, I've used Envy, yes I've used the default installer from ATi for their drivers on my card and correctly edited the conf file. But no matter what I do, I always am forced into low graphics mode at 800x600. Any help would be appreciated, below are my specs:

AMD Athlon 64 3400+ 2.2Ghz
ATi Radeon X1600 Pro 512MB
2 GB RAM
I am running the latest version of Ubuntu (Not Beta)

---

### Post by spiderbatdad on 2008-04-05
could you run the command ```
sudo dpkg-reconfigure xserver-xorg
``` answer the questions by reading the dialogue carefully and using the arrow keys to scroll and select "ok" then enter to enter. Reboot your system and run ```
dmesg
``` read everything carefully, and you might find some configuration problems in the boot process...or copy/paste the output into your gedit text editor. The right click the file and select "create an archive" upload that archive into your next post with the manage attachments tool below the reply window.

---

### Post by Essel on 2008-04-05
Okay, I followed what you said, and here is the result from dmesg.

---

### Post by prshah on 2008-04-05
> **Essel said:**
> Okay, I followed what you said, and here is the result from dmesg.

Also request post of  /var/log/Xorg.0.log (or .1.log or .2.log...) More relevant.

---

### Post by spiderbatdad on 2008-04-05
So, are you still stuck in low graphics?
Or does this happen when you try to enable desktop effects?

Despite what could look like problems in dmesg, due to the reporting messages that where chosen by developers, the output looks ok.

If you still have a problem you could post what kind of laptop your using...I could guess...nah.
Also search google with your issue and including launchpad in the search may lead you to bugs that have been fixed or patched.

---

### Post by spiderbatdad on 2008-04-05
Also in your dmesg where it says :
] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

That looks like a kernel option you could try in the kernel line of /boot/grub/menu.lst
see this post for explanation on how to edit.[http://ubuntuforums.org/showthread.php?t=745093](http://ubuntuforums.org/showthread.php?t=745093)

just scroll down a bit.

---

### Post by Essel on 2008-04-05
So, I followed the instruction in that post, and it's seemed to have done nothing, I've included the Xorg log file you wanted (It's from after doing the stuff in that post). Yes I am stuck in low graphics mode even after booting up, it only lists possible screen resolutions as 800x600 and lower, and I cannot enable any desktop effects.
Also, if it helps, I had to install Ubuntu through the text installer, and then install my graphics driver through envy in recovery mode to even get into the GUI, and it worked (I was able to run at over 1280x1024 no problem) the first time I booted, but this happened after that.

---

### Post by spiderbatdad on 2008-04-05
I was trying to suggest this as a kernel option:
] Nvidia board detected. Ignoring ACPI timer override.
[ 0.000000] If you got timer trouble try** acpi_use_timer_override**
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008

Not the same options from that other post. I'm not sure how to address your situation
though as you have installed envy. Some new ati updates were made available for the latest Hardy kernel. As you are just getting started, anyway, I would recommend Hardy Beta to you, then run all the updates. Hardy will be released very soon.

---

### Post by Essel on 2008-04-05
Oh, sorry, didn't know. Well I'll try the latest beta, and see how that goes. If all else fails, I'll try everything over again on there.

EDIT:
After installing the beta version of the latest Ubunutu, it solved the problem, thanks for the help!

---

### Post by prshah on 2008-04-06
> **Essel said:**
> So, I followed the instruction in that post, and it's seemed to have done nothing, I've included the Xorg log file you wanted (It's from after doing the stuff in that post). Yes I am stuck in low graphics mode even after booting up, it only lists possible screen resolutions as 800x600 and lower, and I cannot enable any desktop effects.
Also, if it helps, I had to install Ubuntu through the text installer, and then install my graphics driver through envy in recovery mode to even get into the GUI, and it worked (I was able to run at over 1280x1024 no problem) the first time I booted, but this happened after that.

Ok you're running into problems because you DONT have the nvidia driver loaded, instead you have the generic VESA driver loaded. Time to re-install the nvidia driver? Or just open your /etc/X11/xorg.conf file, and replace the line > Driver  "vesa" with > Driver "nv"

---

### Post by SunnyRabbiera on 2008-04-06
> **Essel said:**
> Oh, sorry, didn't know. Well I'll try the latest beta, and see how that goes. If all else fails, I'll try everything over again on there.

EDIT:
After installing the beta version of the latest Ubunutu, it solved the problem, thanks for the help!

Just remember that it is a beta so dont expect perfection.
My suggestion is to hold out, there isnt too much we can do as ATI sucks on linux, but then again it doesn't fair much better on windows.

---


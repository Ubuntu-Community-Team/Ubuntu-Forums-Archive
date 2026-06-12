---
title: "Need help with screen resolution"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by llm385 on 2008-04-17
I have been using Ubuntu for a few weeks, and liking it!

Today when I booted my computer, I have a screen resolution of 640 x 480 and no other choice according to screen resolution preferences.  Yesterday I had 1024 x 768.  Can't take this large size!
 
I am not very proficient in Linux.  

I have a Dell 773c monitor, and a Gateway computer with onboard graphics card.

My Windows installation hasn't changed ( is still 1024 x 768 ).  

I also rebooted, but nothing has changed, still 640 x 480.

Laura

---

### Post by northern lights on 2008-04-17
Can you post the output of ```
lshw -C display
``` Thank you.

---

### Post by llm385 on 2008-04-17
laura@laura-linux:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@00:02.0
       version: 03
       size: 128MB
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: driver=i810_smbus latency=0
       resources: iomemory:f0000000-f7ffffff iomemory:ffa80000-ffafffff irq:17

---

### Post by northern lights on 2008-04-17
This appears to be a known issue.

In the BIOS, you may have an entry that allocates memory to the integrated video. It should have options for 1MB and 8MB. Should that be set to 1, switch it to 8 and see what happens.

---

### Post by llm385 on 2008-04-17
The page buffer is set to 8 already. Just checked.

---

### Post by spiderbatdad on 2008-04-17
you can try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` If you have enable compiz or composite windows manager, this command will disable it. It will also attempt to rewrite the /etc/X11/xorg.conf file, and reconfigure detected hardware settings.

---

### Post by northern lights on 2008-04-17
Crap. I'm dumbfounded.

It appeared to me your card was lacking memory and thus defaulting to VESA standard. Now I dunno why.

---

### Post by Zralou on 2008-04-17
My Hardy install did the same thing right after an update.  I had to re-install the video drivers and manually edit the xorg.conf file to add the resolutions.

Sara Lou

---


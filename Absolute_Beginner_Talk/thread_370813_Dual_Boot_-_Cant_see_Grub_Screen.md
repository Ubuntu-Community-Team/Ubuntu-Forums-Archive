---
title: "Dual Boot - Cant see Grub Screen"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jakc on 2007-02-26
Hi. I have installed Ubuntu on a separate partition using the wizard with the installer cd (ubuntu-6.10-desktop-i386).  Everything ran smoothly, however I am havign trouble with the initial grub screen.  

When booting, after the usual BIOS settings, a screen does flash up saying Grub Loading, but then my monitor (sony x-black) displays the message:
> 
Out of Range
35.5khz/4Hz

This also happened with the live cd trial.  However, after 15seconds or so, the Ubuntu destop will then load up.  However, I now cant access my Windows OS.  

Is this problem common?  I would also like to make Windows load by default, but still be given the GRUB screen to choose which OS to run.  Any ideas?

---

### Post by halitech on 2007-02-26
sounds like whatever the default settings are for the boot screen that the video card is using, are out of the range that your monitor can handle. You might try reconfiguring your Xorg.conf file but I'm not sure what to change for sure. What video card do you have? might help for someone else to give you the correct info/settings.

---


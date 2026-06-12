---
title: "Tons of problems installing Edgy on my desktop"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ski309 on 2007-04-11
I am working on using Ubuntu on my desktop as a media center for my HDTV, but I've been running into a slew of problems.

1) When I install Edgy, I tell it to install GRUB on (hd0).  Yet, when I boot my system and select a Linux kernel, it says "partition not found".  When I press 'e' to edit that particular boot sequence, the GRUB commands show (hd2,1).  I have to change that to (hd0,1) and then GRUB will boot.  I've learned to edit the menu.lst file to permanently change the boot sequence to hd0, but whenever I install a new kernel module, or anything that would make GRUB update menu.lst, the commands revert to (hd2,1).  So, how do I make it stop doing that? In case you ask, I have several different drives:
a) 74GB SATA Drive (where windows and linux are installed)
b) 250GB IDE Drive (for windows programs)
c) 500GB SATA Drive (for media)

2) My computer has an NVIDIA 7900GTX card installed, and the 'monitor' is a Toshiba 52HM84 HDTV.  Last night I tried to bring the resolution up from 800x600 to the TV's max resolution of 1920x1080i, using a modeline, but I was only semi-successful; the resolution only increased to 1280x720.  How can I set it to 1080i?  I think I read somewhere that you're supposed to be able to change the resolution on Nvidia cards using their proprietary drivers and nvidia-settings, but I haven't been able to find it.

2a) Also, since the TV doesn't have controls to adjust overscan, I need to use other means.  I tried NvTVOut (I think that's the name) but that wouldn't even run.  I tried xvidtune but every adjustment I attempted was considered incorrect.  Any suggestions?

3) My sound disappeared.  I heard the login sounds at one point but they disappeared, and I don't know why.  I have a SB Audigy 2 card install, and the motherboard has onboard sound but that is disabled through BIOS.  Is Edgy trying to output to the onboard sound even though it's disabled?  If so, why was the sound working before and now it's not?  More importantly, what can I do to fix it?

Annoyances:
1) How do I get rid of all the extra GRUB choices?  I just want the latest kernal I'm using (+ the recovery mode) and Windows.

---

### Post by eljalill on 2007-04-11
Sorry only have a suggestion to one question and a very simple one at that:
Sometimes the sound gets turned down. The Master than can still be up, but you wouldn't here anything, if everything else is down.
Check in Alsamixer (typer alsamixer into terminal) or double click on sound item in panel to double check.

best of luck!

---

### Post by dstew on 2007-04-11
For your first question, why does grub choose the wrong root, you can edit the /boot/grub/menu.lst file. Find the line that says 

**# groot=(hd2,1)**  and change it to

**# groot=(hd0,1)**

Do not "uncomment" the line.

---

### Post by dstew on 2007-04-11
For problem #2, have you installed the proprietary nvidia driver yet? It does not come already installed, since it is not open source.

The easiest way to install it is to use the Envy script: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by dstew on 2007-04-11
For your Annoyances, just remove your old kernel installations using Add/remove programs or Synaptic. When you remove the old kernels, the uninstaller will automatically remove the grub menu.lst entries for those old kernels. That said, it is usually a good idea to keep the next-to-most-recent kernel in place, just in case something weird happens with a new kernel.

---

### Post by ski309 on 2007-04-12
The groot thing worked, thanks dstew!

I was able to figure out #3, I had to set the default soundcard to my Audigy Card in System/Preferences/Sound, second tab.

I installed the proprietary nvidia driver last night.  I had to do it manually because the Envy script errored out.
I editted the xorg.conf to include several of the things found [here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-h.html").  I'm at work right now so I can't give you my exact xorg.conf until later.

---


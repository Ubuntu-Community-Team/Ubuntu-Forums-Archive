---
title: "Installation problems round two (no video)"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by MarkSparks on 2007-08-02
Again, here are my specs :

AMD Athlon 64 X2 4600+ Windsor 2.4GHz Socket AM2 Processor Model ADA4600CUBOX - Retail
GIGABYTE GA-M55SLI-S4 Socket AM2 NVIDIA nForce4 SLI ATX AMD Motherboard - Retail
G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop
EVGA 320-P2-N811-AR GeForce 8800GTS 320MB 320-bit GDDR3 PCI Express x16

And my monitor is a Dell 2405fpw 24" LCD using the DVI connector. 


I can get the live CD to load by doing the F4 at boot menu. I select 1600x1200 resolution and it comes up fine. Ubuntu 7.04 seems to install fine until I get to the point where it drops back to the logo screen and says remove CD from tray and hit Enter to reboot. 

Enter is unresponsive on both a PS/2 and USB keyboard. 

I restart it with the front reset button, I get past the bios screen, to the enter "esc" for boot menu and the screen just goes black. No HDD activity, nothing. I tried waiting about 5 mins and then inputing my username and password to see if the GUI would switch over to a useable screen, but nothing. 

I then hit escape and did the recovery mode install, got to the user prompt, leading to me to believe this is a video issue, not an problem with copying files during installation or the like...

I run the reconfigure for xserver and I enable the 1600x1200, 1024x768 resolutions (1600x1200 is what I used for installation), it states that it overwrote my exist xconfiguration, I do a command line reboot....

After rebooting, the same thing, black screen of unresponsiveness. I let it go for a while and try to log in blindly, nothing, no music, no anything. I tried to drop to terminal with CTRL+ALT+F1, nothing. Perhaps of note, when I'm at the user prompt in recovery mode, when I reconfig xserver, I couldn't do a startx or CTRL+ALT+backspace. 

Anything else I could try? I had to reload Vista and I hated every moment of it.

---

### Post by Raineer on 2007-08-02
> I get past the bios screen, to the enter "esc" for boot menu and the screen just goes black. No HDD activity, nothing. I tried waiting about 5 mins and then inputing my username and password to see if the GUI would switch over to a useable screen, but nothing.

I then hit escape and did the recovery mode install,

Ok, we'll need some careful information here.

In your first example, you pressed ESC to get to the boot menu and it just goes black.
In your second example ESC actually works since you are able to get to the recovery mode.

Those 2 are mutually-exclusive so we need to determine where the failure is.  In your first example, are you able to select Ubuntu-Kernel 2.16  or whatever it says...and THEN it goes black with no response?

If it's just a video problem you'd be pretty far in, and you could boot into recovery mode and look at xorg.0.log and see where the problem lies.  With an xorg problem, you should still be able to Ctrl-Alt-F2

---

### Post by MarkSparks on 2007-08-02
If I let it boot naturally or choose the "non-recovery" mode, it goes black and hangs. 

If I go into recovery mode, I can get to the user prompt. 

When it booted up to the non-recovery version of the kernel is when I tried to do the CTRL+ALT+F1... I didn't try F2, but I did try with F5... just trying to mash random CTRL+ALT+Function keys. F2 was probably one of the only ones I didn't try.

---

### Post by MarkSparks on 2007-08-02
Anyone?

---


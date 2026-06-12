---
title: "Ubuntu Studio and/or Real-Time Kernel in MBP 3,1?"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by sunbird on 2008-05-12
I am (perhaps futily) trying to get Dragon Naturally Speaking running on an Windoze XPSPII guest in VirtualBox 1.6 (non-OSE) on my 8.04 install. I have heard from several folks that I need to install the real-time kernel to get the mic to work properly** in the guest OS (even though the mic works fine in Ubuntu), but my last results installing this kernel were disastrous (constant kernel panics). I'm wondering if I might have better results if I install the full set of Ubuntu Studio custom packages (which includes the -rt kernel), but wanted to check here first.

So, has anyone run the -rt flavor on a Macbook 3,1 with good results? More specifically, any experience running Ubuntu Studio on Macbook 3,1? Finally, if by some bizarre chance someone has actually run DNS in this situation, I'd love to hear from you.

*** The USB mic shows up in Windoze, and audio is routed there, but there is some trouble with the sample rate -- the audio is garbled. The audio is **not** similarly garbled in Ubuntu.*

---

### Post by cyberdork33 on 2008-05-12
The rt kernel has major issues on Macs for some reason. At least it has in the past. I don't think that any other supporting packages will change that.

Just try installing it... If you still get kernel panics galore, just choose your previous kernel in Grub, and remove the rt kernel. No harm done.

---

### Post by sunbird on 2008-05-12
That's good to know, but really too bad since I think it is the reason that I can't get DNS working. Do you know of any other solutions to the mic sample rate issue? 

I've attached a sample recording illustrating the issue.

---

### Post by sunbird on 2008-05-12
Okay, how about a more basic question. If I plug the microphone directly into the MBP's mic-in jack (i.e. bypassing the USB), which channel does it show up on in ALSA mixer? I think I've tried them all and can't get any of them to produce sound.

---

### Post by cyberdork33 on 2008-05-12
should be "line-in" or similar. Here is usually an associated "Capture" channel that also needs to be adjusted.

---


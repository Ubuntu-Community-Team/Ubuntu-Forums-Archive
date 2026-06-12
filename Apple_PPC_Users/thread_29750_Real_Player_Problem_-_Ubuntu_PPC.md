---
title: "Real Player Problem - Ubuntu PPC"
date: 2005-04-25
forum: Apple PPC Users
---

### Post by usr3301 on 2005-04-25
I had Real Player 10.0.4.750, installed and partially working. For some reason, when playing video clips (local to the HDD even), the video was very choppy. I checked my CPU and it was no where near 100%. I was unable to correct the problem, so I decided to try and earlier version. I deleted (manually) the realplayer directory and links. I then installed 10.0.0.297. When trying to run this version, I receive the following errors:

** (realplay.bin:6142): WARNING **: Unknown property DistCode in config file

** (realplay.bin:6142): WARNING **: Unknown property OrigCode in config file
/usr/local/bin/RealPlayer/realplay.bin: relocation error: /usr/local/bin/RealPlayer/plugins/swfrender.so: undefined symbol: _Z27FlashRendererCreateInstancePP8IUnknown

I then, again, manually deleted realplayer and re-installed 10.0.4.750. When trying to run this version, I again get the above errors.

I am at a loss. Can anyone tell me how to fix these errors and make Real Player run again? Also, once it is running, what can I do about choppy video?

Here is my system information:
Hardware: PowerBook G4 Aluminum, 1.5GHz, 512MB RAM
Video Driver: ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)
OS: Ubuntu Linux Hoary (5.04)
Kernel: 2.6.10-5-powerpc


Thank you!

Bryan

---

### Post by tbfr on 2005-04-25
it should work after removing swfformat.so and swfrender.so from your plugins folder. 

cheers,

tobi

---

### Post by usr3301 on 2005-04-25
Removing those plugins solved the problem with starting Real Player.  The video playback is still extremely choppy though.  The sound is fine, but video plays a second or two, then freezes for a few seconds and continually does this.  Any ideas?  Thanks again for your help!!!

---

### Post by Sly_R on 2005-10-25
I'm having a similar problem;  audio is choppy and controls are slow to respond.

There shouldn't be a problem with my 'puter.  Any ideas?

---

### Post by seatea on 2005-10-27
I have PM G4 400 that I have been trying to get realplayer to install on  for days. I am new to the Ubuntu OS and completely frustrated by trying to  install realplayer on my system after so many failed attempts. Would you  go over how you installed realplayer? Also, where is the plug-ins folder with swfformat.so and swfrender.so?

---


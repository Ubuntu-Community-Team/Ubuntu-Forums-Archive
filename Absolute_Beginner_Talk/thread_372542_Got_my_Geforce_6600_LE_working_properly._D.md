---
title: "Got my Geforce 6600 LE working properly. :D"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Poman on 2007-02-28
I don't know why, but I was having problems getting my video card to work. I'm running the AMD64 version of Ubuntu, if that matters. If I installed the nvidia-glx or tried the latest drivers from Nvidia I was either not able to get back into Gnome or it never quite recognized my card properly and it didn't give 3D support.

One time from a fresh Ubuntu install I ran the Automatix2 nvidia drivers and it worked perfectly, but after trying the Beryl automatic script with beta Nvidia drivers things got messed up again. I could not get back into Gnome unless I changed the xconfig file to show VESA. 

What I eventually did was to manually remove nvidia-glx in synaptic package manager, and manually install nvidia-xconfig from there as well. Then I ran Automatix2, and something new happened as it appeared to actually overwrite something, and the drivers installed just as well as they had from a fresh Ubuntu install. The only difference is that under Applications-System tools it says now Nvidia Settings instead of Nvidia Xconfig as it had previously. 

Now it recognizes the 6600 LE card in the Nvidia Settings, and even the SyncMaster monitor to a much greater extent. It still doesn't see that it's the SyncMaster 970p monitor precisely, but I had to add the 1280x1024 resolution and manufacturer monitor refresh rates to the xorg.config file anyway. It's all working great now, and I even got Beryl and Kxdocker working nicely! Still there are bugs with Kxdocker it seems, but Beryl is smooth! I installed Beryl manually as well this time to make sure the nvidia drivers would not get overwritten.

Thanks to this forum and other online sources, and enough time spent... I think I'm going to be really happy with Gnome for a while. I also tried Mandriva with KDE and it recognized my nvidia card nicely, but I don't like KDE sadly and Mandriva gave me other problems I couldn't seem to get past. It's just got too much confusing stuff for me. I like the clean look of Ubuntu and Gnome.

---


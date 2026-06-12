---
title: "Sound Distortion"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by earlobes on 2005-11-24
Hey there, I'm a new user of Linux, having installed it for the first (successful) time yesterday on my home computer.

I got everything up and running and managed to find Rhythmbox and proceeded to load my music collection (99% mp3), which didn't work too well. Eventually I managed to install the mp3 codec (I am assuming as mp3's play now, not sure how on earth I managed that though), and again loaded my music collection. Everything worked fine, but I noticed a considerable, borderline intolerable sound distortion coming through with the music.

Incorrectly assuming that it was Rhythmbox, I managed to get XMMS installed and running, with the same distortion problem. I then assumed that the distortion was due to the mp3's being stored on a windows (NTFS) partition, but I noticed that the same distortion, while being harder to detect, was also present in all the little dings and dongs of the system.

Volume levels are on full, and my sound card is an integrated "SiS SI7012" according to the volume control preferences (which sounds about right, however the precise model number was never committed to memory).

Booting windows (XP Professional) gives me undistorted sound and music, so I am pretty sure that its some aspect of Ubuntu causing the problem.

With regards to hardware, the processor is a pentium 4 and theres mostly asus running gear. Asus P4533-X Motherboard, with the integrated SiS SI7012 handling sound.

I have searched wiki's and forums galore but to no avail, many people have similar problems but no solutions have worked for me. I have included as much information about the problem as I can... any tips or suggestions would be greatly appreciated. Sorry for the long post.

Thanks.

---

### Post by Pablo_Escobar on 2005-11-24
Wild guess, go to Volume Manager (Gnome or KDE) and make PCM half way up, not the max. Master volume can be maxed. Steer the volume with speakers, and try it.
Attention : Rythmbox and other music players raise PCM if You don't set the software volume control.

Just try it.

---

### Post by earlobes on 2005-11-24
Thanks, I tried that and it seems to have worked.

---


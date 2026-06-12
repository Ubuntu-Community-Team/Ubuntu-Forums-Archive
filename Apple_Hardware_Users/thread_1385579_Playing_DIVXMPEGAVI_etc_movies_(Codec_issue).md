---
title: "Playing DIVX/MPEG/AVI etc movies (Codec issue)"
date: 2010-01-19
forum: Apple Hardware Users
---

### Post by sthestrup on 2010-01-19
Hi there, I have installed Ubuntu 9.10 (Karmic Koala) on a PowerPC. I would like to use the computer as a media server but so far I have been unable to get any video output. There are sound, and if I try taking a screenshot (VLC, totem) the decoding work but the video is just a blank screen.

I have tried several movie players, including VLC, Gnome's default movie player (totem) and MPlayer. MPlayer do show some video output but its black and white and it has some weird scaling, meaning that it only shows pictures on approx 10% of the horizontal axis.

When searching on google most people suggest using ppc-codecs package from the medibuntu repository. But it turns out that it doesn't exist for Karmic Koala, and the latest version is for Hardy Heron and is impossible to install (as far as i know) on Karmic Koala.

I am no super user so I might not have done everything correctly, but I don't know how where I might be wrong. I really hope someone will help me with this issue.

Please let me know if I haven't supplied enough information.

Thanks in advance!

/Steffen T.

---

### Post by conal on 2010-02-16
Hi Steffen!

here is how I installed the codecs from medibunu on my iMac: 

first get libstdc++5 from here:

[http://packages.debian.org/lenny/powerpc/libstdc++5/download](http://packages.debian.org/lenny/powerpc/libstdc++5/download)

then get the ppc codecs .deb package for mp3's etc from the medibuntu website:

[http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb](http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb)

and then get the .deb package for dvd etc:

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

Save them all somewhere handy, and install them (libstdc++5 first) with GDebi package installer, or from the command line.

This worked on my iMac 'lampy' G4 - It plays most formats fine. The first time I opened an MP4 video in Totem it prompted me to download another codec for AAC, but I had the medibuntu repository enabled in synaptic so that downloaded ok and worked fine.

Some other notes;- 

-if mp3 playback is bad consider removing pulse audio
-if youtube etc is bad consider using a firefox extension to download instead of using the embedded player.
-I could not get VLC working with 9.10 so you might need to remove that and use another player.
-Compositing managers/display effects interfere with video playback
 

Cheers

Conal

---

### Post by rjcalifornia on 2010-02-17
hi!! Install Xine....

sudo apt-get install xine-ui

it plays avi, divx, h.264, flv, etc... 

VLC is broken for ppc and you have to compile it yourself (DONT)

---

### Post by conal on 2010-02-19
Hi RandyVanBuren

Have you tried Kubuntu?

I just installed it - VLC now works fine! It also fixed a mount issue I had with Gnome. Gnome would not mount my music partition or DVD/CD's - at least not automatically - KDE mounts the drives automatically!

For some reason I am having trouble with gxine though - it  drops a frame every coupe of seconds - wish I understood more about these things!!!

Best

Conal

---

### Post by conal on 2010-02-20
Sorry RandyVanBuren- Ignore that last comment - I just noticed you are on Kubuntu - doh! 

I have no idea why VLC is working for me with Kubuntu when it wouldn't with Gnome, XFCE or LXDE.

Best

Conal

---

### Post by bkadoctaj on 2010-05-02
> **conal said:**
> Hi Steffen!

here is how I installed the codecs from medibunu on my iMac: 

first get libstdc++5 from here:

[http://packages.debian.org/lenny/powerpc/libstdc++5/download](http://packages.debian.org/lenny/powerpc/libstdc++5/download)

then get the ppc codecs .deb package for mp3's etc from the medibuntu website:

[http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb](http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb)

and then get the .deb package for dvd etc:

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

Save them all somewhere handy, and install them (libstdc++5 first) with GDebi package installer, or from the command line.

This worked on my iMac 'lampy' G4 - It plays most formats fine. The first time I opened an MP4 video in Totem it prompted me to download another codec for AAC, but I had the medibuntu repository enabled in synaptic so that downloaded ok and worked fine.

Some other notes;- 

-if mp3 playback is bad consider removing pulse audio
-if youtube etc is bad consider using a firefox extension to download instead of using the embedded player.
-I could not get VLC working with 9.10 so you might need to remove that and use another player.
-Compositing managers/display effects interfere with video playback
 

Cheers

Conal

Awesome.  Thanks for this.  :)  I used it on an eMac (USB 2.0) in Ubuntu Lucid with no apparent issues.  I had to use libdvdcss2_1.2.10-0.2medibuntu1_powerpc.deb in order to have satisfactory dependencies.

---

### Post by WARvault on 2010-08-12
> **conal said:**
> Hi Steffen!

here is how I installed the codecs from medibunu on my iMac: 

first get libstdc++5 from here:

[http://packages.debian.org/lenny/powerpc/libstdc++5/download](http://packages.debian.org/lenny/powerpc/libstdc++5/download)

then get the ppc codecs .deb package for mp3's etc from the medibuntu website:

[http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb](http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb)

and then get the .deb package for dvd etc:

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

Save them all somewhere handy, and install them (libstdc++5 first) with GDebi package installer, or from the command line.

This worked on my iMac 'lampy' G4 - It plays most formats fine. The first time I opened an MP4 video in Totem it prompted me to download another codec for AAC, but I had the medibuntu repository enabled in synaptic so that downloaded ok and worked fine.

Some other notes;- 

-if mp3 playback is bad consider removing pulse audio
-if youtube etc is bad consider using a firefox extension to download instead of using the embedded player.
-I could not get VLC working with 9.10 so you might need to remove that and use another player.
-Compositing managers/display effects interfere with video playback
 

Cheers

Conal

Just wanted to say this has worked for me on a iMac G3 400DV indigo running alternate Ubuntu 10.04 install.

---


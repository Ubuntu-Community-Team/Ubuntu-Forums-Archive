---
title: "Totem-xine running but..."
date: 2004-10-24
forum: Apple PPC Users
---

### Post by Castaa on 2004-10-24
Hi all,
   
   I got Totem-xine installed onto my 600 Mhz iBook.
   
   It took the following deb packages to be installed before it would allow me to install totem-xine:
   
   libgpg-error0_1.0-1_powerpc.deb
   libdvdcss2_1.2.8-0.0_powerpc.deb  
   libopencdk8_0.5.5-8_powerpc.deb
   libdvdplay0_1.0.1-6_powerpc.deb   
   libstartup-notification0_0.7-1_powerpc.deb
   libgcrypt11_1.2.0-4_powerpc.deb   
   libtasn1-2_0.2.10-3_powerpc.deb
   libgcrypt7_1.1.90-9_powerpc.deb   
   libgnutls11_1.0.16-9_powerpc.deb
   totem-xine_0.99.16-1_powerpc.deb
   
 dpkg also required me to uninstall totem-gstreamer.
   
 However the DVD video and audio playback is very choppy. But it did play. I'm wondering if the code isn't optimized enough to play video. I know that DVDs played fine when OS 9 was installed on this computer. 
   
   Any suggestions would be great.

---

### Post by Castaa on 2004-10-24
The good news is that CD audio playback works now through the iBook's speakers and via the headphone jack! :D
 
It even plays mp3 right off my iPod via USB.  Nice!

---

### Post by Castaa on 2004-10-25
Update:
 
**hdparm -d1 /dev/hdb**
 
"/dev/hdb" is the path to my iBook's DVD-ROM (this may vary depending on how many drives you have hooked up to your computer.) And -d1 turns on DMA access to the device.
 
 
**hdparm -i /dev/hdb**
 
This will give you info about your drive and will list the I/O modes this device supports. There should be (*) next to current mode the drive is configured to.
 
 
**hdparm -t /dev/hdb**
 
This will test the performance of your drive. You need to have a DVD or CD in the drive for this option to work.
 
Here is more info on setting various mode directly:
[http://www.ziobudda.net/mirror/sxs/housekeeping/hdptune.html]("http://www.ziobudda.net/mirror/sxs/housekeeping/hdptune.html")
 
Turning on UDMA2 for the DVD-ROM is important. The video and audio playback is improved but DVD playback is still skipping frames and audio is 'clicking' and it's slightly out of sync with the video during playback. 
 
I think the DVD decoding is too demanding on my 600 Mhz CPU. 
Since top is reporting near 100% CPU usage during playback. :( 
 
*What file do add this line so it sets the DVD-ROM to UDMA2 at boot up?*

---

### Post by bewilkinson on 2004-10-26
"However the DVD video and audio playback is very choppy. But it did play. I'm wondering if the code isn't optimized enough to play video."

It is much more likely that the linux video drivers are unable to make use of your mac's dvd mpeg2 decoder built into the video chip, therefore linux is using your CPU instead.

---

### Post by Castaa on 2004-10-26
Ya, that might be it. I know that 3D acceleration isn't supported with the r128 drivers, mpeg2 probably decompression isn't either. :cry: Sadly no upgrading the video card either I imagine.

---

### Post by TekMate on 2004-10-29
Totem-xine doesn't work well for me either but gxine flys with no issues movie is fast and clear.

---

### Post by Castaa on 2004-10-30
[QUOTE=TekMate]Totem-xine doesn't work well for me either but gxine flys with no issues movie is fast and clear.[/QUOTE] 
Cool.  Thanks for the info.  What hardware are you running gxine on?  Thanks! O:)

---

### Post by Castaa on 2004-10-30
Woot!  I installed gxine and DVDs are playing correct for the first time under Linux ever on my iBook!  Thank you for gxine tip!!!!
 
a few of minor problems:
 
1. When I set the DVD to play in full screen mode gxine crash after a few seconds of full screen play back.  But only in full screen mode.  I can maximize the window
 
2. I'm getting a popping sound when DVD play loud sounds.  I tried adjusting the volume but even at low volume I hear audible 'pops' or 'clicks'  It seems like the audio is clipping.
 
3. The audio during DVD play back is synced with video but the audio seems seems play at a lower frequency.  All audio is deeper sounding that it should be.

---

### Post by TekMate on 2004-10-30
[QUOTE=Castaa]Cool.  Thanks for the info.  What hardware are you running gxine on?  Thanks! O:)[/QUOTE]
 An 867mhz powerbook with 512mb of ram.

1. Your right I always play in a window and never noticed that before.
Do an apt-get install xine-ui and you can use regular xine instead it doesn't suffer from the same issue.

2. I'm not hving this issue do you have sound maxxed? try setting it to 90% does it still do it?

3. Certain DVDs I notice this as well not sure what the cause is as I haven't noticed it on CDs and other audio.

---

### Post by Castaa on 2004-10-30
1. Your right I always play in a window and never noticed that before.
Do an apt-get install xine-ui and you can use regular xine instead it doesn't suffer from the same issue.
 
Again great suggestion.  xine-ui plays full screen without the crash!
 
 
 
2. I'm not having this issue do you have sound maxxed? try setting it to 90% does it still do it?
 
Yes it happens at all sound levels.  Even if I lower the DVD audio volume or the system volume.  Same result.  This is the last remaining irritating problem.
 
 
 
 3. Certain DVDs I notice this as well not sure what the cause is as I haven't noticed it on CDs and other audio.
 
Yes it's only with DVD audio.  CD audio is fine.  It doesn't seem as bad with xine-ui.  That could be just my imagination though.

---

### Post by TekMate on 2004-10-30
[QUOTE=Castaa]1. Your right I always play in a window and never noticed that before.
Do an apt-get install xine-ui and you can use regular xine instead it doesn't suffer from the same issue.
 
Again great suggestion.  xine-ui plays full screen without the crash!
 
 
 
2. I'm not having this issue do you have sound maxxed? try setting it to 90% does it still do it?
 
Yes it happens at all sound levels.  Even if I lower the DVD audio volume or the system volume.  Same result.  This is the last remaining irritating problem.
 
 
 
 3. Certain DVDs I notice this as well not sure what the cause is as I haven't noticed it on CDs and other audio.
 
Yes it's only with DVD audio.  CD audio is fine.  It doesn't seem as bad with xine-ui.  That could be just my imagination though.[/QUOTE]
 Your iBook is that a G3? I wonder if it doesn't have the power for audio. Just throwing out straws as I'm not sure. Have you googled it using Debian? It may be a known issue with that model.

---

### Post by chascon on 2005-01-08
"Re: Totem-xine running but...
Ya, that might be it. I know that 3D acceleration isn't supported with the r128 drivers, mpeg2 probably decompression isn't either. Sadly no upgrading the video card either I imagine."

What are you talking about Castaa?  I got the Rage 128 working with accel.
You need to replace the xserver with daenzer's trunk version and remove xscreensaver along with some screensavers to get accel working without your computer crashing.  It's all detailed in the ppc thread labelled "Re: ATi Rage 128 and DRI".

---


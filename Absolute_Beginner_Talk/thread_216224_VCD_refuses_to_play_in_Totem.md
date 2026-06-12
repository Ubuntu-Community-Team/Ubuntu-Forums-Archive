---
title: "VCD refuses to play in Totem"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by bludhound on 2006-07-15
Hi friends.

After a long decision, I have finally decided to shove Windows aside and switch fully to Ubuntu. So for the past few weeks, I have been learning my way around Linux and at the same time tuning my BIOS settings to get best results with Ubuntu. Finally, I decided to do a clean installation of Ubuntu once again and set things up properly.

I began to configure Totem to use Xine instead of GStreamer. I installed the libdvd* packages. I installed the libxine-extracodecs package as well.  All went well, and I got my video DVDs running good, until I tried to place a VCD into my drive. As per expected, Totem opened up automatically to try to play my VCD. However, Totem did not load the video, and displayed the following message instead:

Totem could not play 'vcd:///media/dvdrecorder'.
There is no input plugin to handle the location of this movie

Feeling persistent to get Totem to work, I installed the libvcdinfo0 package. No luck, still. Next, I tried to open the VCD using 'Movie / Play Disc (name of my VCD)' in the Totem menu. I got a different message from this:

Totem could not play this media (Video CD) although a plugin is present to handle it.
You might want to check that a disc is present in the drive and that it is correctly configured.

For easy reference to those who are trying to help me, there are the relevant libraries I have installed:
totem-xine
libxinerama1
libxine-main1
libxine-extracodecs
libvcdinfo0
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3

And here is a summary of the problem:
I use Drapper Drake, GNOME.
DVD works in Totem, VCD doesn't.
Tried various different VCDs, none work.

Another point I may add is that VLC has no problem playing my VCDs. And why don't I use VLC? It's because I want my VCDs to play automatically upon insertion. I know I can configure the program I want to play DVDs with, but I can't seem to be able to configure it for VCDs. Alternatively, I would be glad too if anyone can tell me a way to change my default program for playing VCDs.

Thanks in advance for those who are willing to help. If there is any other info I have to provide, I will.

---

### Post by Kobalt on 2006-07-15
I believe VCDs work with Gstreamer0.10... Have you installed Gstreamer libs in synaptic ?

---

### Post by bludhound on 2006-07-15
> **Kobalt said:**
> I believe VCDs work with Gstreamer0.10... Have you installed Gstreamer libs in synaptic ?
Hmm.. I got a different error message with Totem-Gstreamer:

Totem could not play 'vcd:///media/dvdrecorder'.
No URI handler implemented for "vcd".

Now my DVD menu refuses to load as well, but I understand that Gstreamer does not support DVD menus.

Another point to add is that my VCDs actually worked in xine-ui. Both xine-ui and Totem use the same engine, so the problem probably lies with Totem.

---

### Post by bludhound on 2006-07-15
I've found out how to change the default VCD application. For those who are interested, enable GConf under 'System Tools' in the Alacarte Menu Editor. Next open GConf and look under /desktop/gnome/volume_manager/autoplay_vcd_command. Edit the settings there.

Now I can trash Totem. But.. I am still curious on why Totem can't play my VCDs.

---

### Post by truantology on 2006-07-15
I have a lot of problems with totem...i got fed up and installed VLC media player.  It plays virtually anything I have!

---

### Post by Kobalt on 2006-07-15
I don't use Totem as well, I've installed MPlayer for firefox plugins, and I alos use VLC to play any kind of video. I think Edgy Eft should bring us a more suitable Totem, or at least a whole bunch of plugins to make it more feature-full...

---

### Post by bludhound on 2006-07-15
I've decided to go for xine-ui as my main player as it seems more user-friendly. The next decision I'll be making is on whether to install Realplayer or not.

---

### Post by BE(Hons)Computing on 2006-09-21
here vlc is also not working. And totem is pain. I installed xine gui and libs. Atleast i am able to see the video but i still have problem with the audio while watching a vcd. And real player is not so useful. Even if i have to listen to the songs i prefer playing it in xmms. Real player is not supporting play lists facility in my pc. Any help for my multimedia section else i have to switch back to mandrake may be windows.

---

### Post by *georg on 2006-10-12
bludhound,

I have exactly the same problem as you described in the original posting. DVDs run fine, VCD, SVCD, CVD (ie., all teh CD-based movie formats) produce error messages as you described.

A few additions: First, this wasn't always the case. Totem used to play VCDs just fine until a while ago (don't ask me when exactly that changed, but it might well have been during the switch from breezy to dapper). Second, mplayer seems to have the same problem, playing DVDs and all kinds of media files, but failing VCDs. Third, I created a VCD the other day, and totem did play the mpeg-stream which served as the base for the VCD just fine, but after burning it didn't play the VCD containing that stream.

Did I understand you right that xine itself (with its own graphical UI) plays VCDs? Because totem, as I have it installed, is -- same as for you -- based on xine.

---


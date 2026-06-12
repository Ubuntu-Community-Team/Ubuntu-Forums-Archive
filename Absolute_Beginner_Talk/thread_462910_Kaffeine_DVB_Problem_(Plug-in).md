---
title: "Kaffeine DVB Problem (Plug-in???)"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by mr_boo1711 on 2007-06-03
Hi guys!

Installed Ubuntu late last year but haven't used it for a few months due to other commitments. :(

Glad to say i'm back to wrestling with it, and enjoying it more than ever now that I have a little time on my hands! :)

Enough of the babble - down to business....

I have a Freecom DVB tuner USB stick, and after updating Ubuntu and installing Kaffeine and a few other bits 'n bobs Ubuntu recognised it and everything looked as though it would be pretty painless.  I scanned for channels and it listed them all - which brought a smile to my face - but when I tried to watch one of the channels it spat an error at me regarding a plug-in...

No plugin found to handle this resource (/home/steve/.kaxtv.ts)

12:37:49 PM: xine: couldn't find demux for >/home/steve/.kaxtv.ts<
12:37:49 PM: xine: found input plugin : file input plugin
12:37:49 PM: video_decoder: no plugin available to handle 'XviD'
12:37:49 PM: xine: found demuxer plugin: AVI/RIFF demux plugin
12:37:49 PM: xine: found input plugin : file input plugin

Now I am still a newbie so go easy - but I do suspect this has an easy answer[?]  I even installed the kaffeine-xine but it didnt help any.

Ideas? - thanks in advance guys/girls.

Steve

---

### Post by TrompeLaMort on 2007-06-03
To play dvds you need to make sure you have the libdvdread and libdvdcss packages installed. 

See [this link]("http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html")

 If you have those installed, check to make sure all libxine packages are installed (I got the same error, went into the adept package manager, and had to install libxine-plugins, and libxine-extracodecs to make it work).

---

### Post by mr_boo1711 on 2007-06-04
> **TrompeLaMort said:**
> To play dvds you need to make sure you have the libdvdread and libdvdcss packages installed. 

See [this link]("http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html")

 If you have those installed, check to make sure all libxine packages are installed (I got the same error, went into the adept package manager, and had to install libxine-plugins, and libxine-extracodecs to make it work).

Nah, its not DVDs that's causing the problem - its Kaffeine's inability to display the audio/video feed coming from my TV USB tuner.  It knows the adapter is there and it scans for channels no probs - it just wont give me any video or sound.  I'm pulling my hair out...

It MUST be something simple I reckon - I just dont have the knowledge... :(

---

### Post by Jzombie on 2007-08-29
Check if you have libxine1-ffmpeg installed.  I had exactly the same problem - same error message.  After spending (too much) time researching this on the internet I used Synaptic package mgr to browse through the xine packages I hadn't installed.  Reading the notes for libxine1-ffmpeg, the last couple of paragraphs read:

This package contains the ffmpeg input plugin for xine, which enables
xine-based players a large variety of modern audio and video
codecs. It also includes some other plugins handling mpeg codec variants.
You most probably want to install this codec.

...I took the hint and installed.  Hey presto - Kaffeine is fully functional with my VisionPlus (TwinHan) USB DVB-T.  OK so your hardware is different, but hey - same error message.

P.S. Ubuntu + Kaffeine - so much better than XP + VisionPlus software.  No dropped frames, smooth video - even while I was updating Ubuntu!

---

### Post by Bristol Rogue on 2008-04-28
Not sure why the system won't let me give you thanks, but thankyou anyway - your solution works!

---


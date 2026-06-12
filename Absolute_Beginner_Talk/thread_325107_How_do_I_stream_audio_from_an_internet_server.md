---
title: "How do I stream audio from an internet server?"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Phenom on 2006-12-25
Hello,

I'll cut to the chase.

I am fairly new to Ubuntu(Linux) and when I used Windows XP I would listen to a Internet radio show called Coast to Coast, I would use Winamp to play the live stream and use Shoutcast to listen to the radio station on my PSP (Playstation Portable).

But I can't figure out how to do this in Ubuntu.

My problem starts with playing the live stream from the Coast to Coast website, I have 2 options, Windows Media Player or Realplayer, I can get VLC to play the WMP version and RealPlayer to play the RealPlayer version, but I cannot figure out how I could allow my PSP to connect to my Ubuntu PC to listen to this live audio from the Coast to Coast website.

I would greatly appreciate any suggestions, help, or guides for this issue. Everyday I fall alittle more in love with Ubuntu and I really feel free while using it compared to Windows XP Pro.

I COULD do this with just using VMWare and running the live stream out of a virtual Windows XP drive but I really am trying to rid myself of Windows. Please can someone help me? Thank you :)

---

### Post by K.Mandla on 2006-12-25
(Moved to Absolute Beginner Talk. :) )

---

### Post by mykalreborn on 2006-12-25
there are a few apps to do this:
 - amarok. a great music player with shoutcast and internet stream support, but with a kde interface - which doesn't fit with ubuntu's gnome: [link]("http://amarok.kde.org/")
 - exaile. basicaly the same script as amarok, but for gnome. can also play shoutcast and internet streams:[link]("http://exaile.org/")
 - songbird. pretty good player, but still in beta version. still it's a good choice for playing internet streams, especially since it can play video streams:[link]("http://songbirdnest.com/")
 - vlc media player:[link]("http://www.videolan.org/vlc/")
 - stream ripper, a good player since it can save internet streams of any sort:D:[link]("http://streamripper.sourceforge.net/")

so there is a whole range of posibilities, without all that mockering with closed source ware ;).
if you have any problems installing these apps do reply. 
ps. amarok can be installed from applications>add/remove programs. the others have to be downloaded from their sites and installed manually.
 hope it helps!

---

### Post by eeried on 2007-01-08
> ... the others have to be downloaded from their sites and installed manually.

VLC, MPlayer are in the Ubuntu  multiverse repository. Mplayer too can record streams very easily.

---

### Post by Kougaiji on 2007-02-22
Rather than start a new topic, I need to expand on this one. I have Songbird, installed just fine AFAIK, and it plays music on my computer without a problem. But when i try to stream from the net it just says "error" next to the progress bar at the top of the window - yes, these files are NOT dead because I CAN download them and I can stream them if I use Windows. Any possible solutions?

---

### Post by mykalreborn on 2007-02-23
> Rather than start a new topic, I need to expand on this one. I have Songbird, installed just fine AFAIK, and it plays music on my computer without a problem. But when i try to stream from the net it just says "error" next to the progress bar at the top of the window - yes, these files are NOT dead because I CAN download them and I can stream them if I use Windows. Any possible solutions?

songbird is still in beta version so that's why it says error. usually it plays internet files without problems, but maybe these ones were encoded differently.

---


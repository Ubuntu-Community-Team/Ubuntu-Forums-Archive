---
title: "Video bad and no sync with audio"
date: 2013-10-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by olli-sylvanne on 2013-10-30
Have ASUS eee PC 1101HA with Atom processor, with GMA500 display driver, Ubuntu 12.04. 

When running HD-videos, MP4, MOV, AVI, the sound runs much faster than video. From case to case the video runs smoothly but not in sync, or on some videos updates the picture once in 10 sec with sound cracking or then it might be anything in between. Cannot find any consistent behavior. Am using Gnome MPlayer, which seems to be the least bad of the gang. VLC player does not work, Movie player is no better. Somebody proposed Pixielive. Anything there?

Now to wake you up: in Windows 7 sound and picture were always in sync. Might happen that driver could not keep pace and the picture fragmented, but mostly all videos ran ok. Now is Ubuntu so much worse? 

Except video, all else runs fine, even USB download is over 20 MB/sec (or Mb/sec), in WIN7 10. WIN7 was terribly slow in most areas.

---

### Post by TenPlus1 on 2013-10-30
First the Asus netbook isn't the fastest available and is sorta built for battery life over power, second the GMA500 graphics on linux isn't the best out there whereas your Windows7 has the actual driver which can decode HD movies a little better than linux's own driver...  Try using something like VLC to play your videos with Hardware Acceleration enabled to see if that helps, and definitely update to Xubuntu 13.10 to gain the latest driver base for your device which will help a lot...

---

### Post by sudodus on 2013-10-30
Hi olli-sylvanne,

You have Lubuntu in the prefix, write Ubuntu in the text and *TenPlus1* suggests Xubuntu.

Unfortunately the free graphics drivers for linux are not as well optimized as the Windows drivers. This can be compensated using a desktop environment with a small foot-print. ***Lubuntu*** is the lightest of the Ubuntu flavours. Xubuntu is medium-light. Unity and KDE are fancy but the foot-print is big, they need a lot of horsepower and memory to run well.

You can also improve playing video using a lighter or more efficient video player. ***mplayer2*** runs well for me.

If you are playing your own videos (from your own camera), it is possible to make a copy with lower resolution (width x height) with for example ***ffmpeg***, to get a resolution that works well in your computer. Keep the original video clips, because your next computer might be able to play them in full HD :-)

---

### Post by olli-sylvanne on 2013-10-31
Thanks. Maybe the difference in driver quality Ubuntu vs Win7, as you said is the the root of slowness. I find it appalling that most applications do not care to sync audio and picture automatically (like Gnome Mplayer). Mplayer2 does.

I need Libre Office, that is why stick to Ubuntu. Could Ubuntu 13.10 be any better driverwise?

And VLC player does not work at all. When I start it, nothing happens. Crash?

---

### Post by sudodus on 2013-11-01
Libre Office is independent of desktop environments, so you can run it in Lubuntu and Xubuntu. You need not run Ubuntu with Unity, if that desktop environment needs more horsepower than what is in your computer. Instead you can ***backup*** your system or at least your personal files and 

- install Lubuntu or Xubuntu and install Libre Office into that operating system

- install a light desktop environment into Ubuntu and select it at the login screen. Click on the round symbol near the window where to enter the password to select 'session' alias desktop environment!

```
 sudo apt-get install lubuntu-desktop
```
or
```
 sudo apt-get install xubuntu-desktop
```

or if you only want to desktop environment (without the full Lubuntu or Xubuntu specific software and tweaks)

```
 sudo apt-get install lxde
```
```
 sudo apt-get install xfce4
```

-o-

Maybe it helps to remove and [re]install VLC. But if mplayer2 works well, isn't that enough?

---

### Post by olli-sylvanne on 2013-11-01
Thank you very much for advise. I'll try one of these desktops.

I am no expert, may be in error, but have tested very many video players. Most do not sync audio and video. Installed VLC many times, does not work. Mplayer2 works best for me, syncs every time, but repetition rate is often 1/sec or similar. With WIN7 it was totally different, most videos ran smoothly.

As I said before, otherwise Ubuntu is superior. F-keys do not work, no big issue, but this hypernition or whatever works ok.

What about the next version after 12.04, worthwile trying?

---

### Post by sudodus on 2013-11-01
You can easily try other versions live (booted from a USB drive, without installing anything). I would not install it without trying it first. In that case I would try the ***new Lubuntu 13.10 i386*** iso file.

But I think ***Xubuntu 12.04 LTS, Precise Gnome Classic Tweaks, LXLE or Bodhi Linux*** (all based on Ubuntu 12.04 LTS) are the best alternatives. (Lubuntu 12.04 has passed end of life, because it had no long time support (LTS).)

---

### Post by olli-sylvanne on 2013-11-01
Hello again

Ran this command line: 
sudo apt-get install xfce4

A lot of download and installation occured then, but there is no xfce4, only the old desktop (did restart several times). I also lost MPlayer2 and there is now Mplayer.

Have I missed something, like some other terminal command?

Would you have time for another piece of advixe?

---

### Post by olli-sylvanne on 2013-11-01
Hello again
Now got the xfce4 up and running. Thanks. The problem was that at start-up I have no log-in. Had to switch user to come to this roundel.

Multimedia with SMPlayer and Mplayer no better than before. Next install Mplayer2, the I'll see. Anybody interested?

---

### Post by sudodus on 2013-11-01
Did you manage to install mplayer2? And how is it working now?

---

### Post by TenPlus1 on 2013-11-02
Sododus: I recommended Xubuntu for the Parole media player which uses gstreamer codecs instead of Lubuntu's mplayer2 arrangement because that's what was causing the sync problem for Olli, also having vlc player as a backup doesn't hurt...

---

### Post by sudodus on 2013-11-02
Good, if you know that Mplayer2 is the problem, it is worth trying Parole. (I might have misunderstood Olli's posts.)

---

### Post by olli-sylvanne on 2013-11-02
We'll this morning after several weeks of trial-error I got the videos working roughly at the same quality as under Win7. No difference if I was on Unity side or xfce side. I was happy.

 Then I restarted the computer and I am again at point A. Videos do not run, audio is cracking. Time runs at double speed even if I have time set as normal (2 places). I am not qualified to understand this - too many variables and maybe Linus/applications instabilities. Besides there are:
video codecs
audio  codecs
audio pulse or alsa and whatever
video gl, x11 and whatever
video sync 2 different to select
demuxer??
deinterlace, rendering and whatever ****.

This is beyond me, I give up.

Thanks for help.

---

### Post by olli-sylvanne on 2013-11-02
Hello guys, only now noticed your comments. Have tried Parole before, no good. And cannot get VLC-player working. Can install it allright but when I launch the media nothing happens, VLC disappiers, probably crashes.
In my opinion MPlayer2 is the most promising for my case.

---

### Post by sudodus on 2013-11-02
Your system might have worked before reboot, because the data was in RAM (fast memory). I think you have too little horsepower in the cpu and gpu to run high definition graphics.

One possibility is to reduce the resolution and  or bitrate of the video. Some video encodings are easier to play (take less cpu or gpu power). This can be done with several tools, for example ffmpeg. There are also GUI tools if you prefer that, for example openshot or avidemux.

If you want to continue along such routes, you can get more details from several other people. It might be worthwhile starting a new thread with a good descriptive title in the sub-forum [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") in order to catch the attention of the multimedia gurus.

---

### Post by SeijiSensei on 2013-11-02
I think you're just running up against the limitations of the hardware.  When I bought an ASUS EEEpc I specifically chose the 1201N because it had an NVIDIA ION adapter that runs VDPAU.  The standard Intel card in Atom netbooks just isn't up to snuff.

That said, your performance is going to depend markedly on the types of media you watch. H.264-encoded content is so highly compressed that little Atoms cannot expand the material fast enough to keep up.  Hi10P content is entirely out.  I doubt you'll be able to watch much past 720p either.  Older MPEG4 material like DivX/XviD in the AVI container should pose many fewer problems.

By the way, smplayer+mplayer2 has been my standard video platform since the latter forked from original mplayer project.

---

### Post by olli-sylvanne on 2013-11-02
Under Win7 I could run most videos without problems, except .MOV, which was outside the envelope.

Thanks and bye, was interesting.

---

### Post by TenPlus1 on 2013-11-03
Out of curiosity, reboot and hold down SHIFT key to enter grub boot menu and select the MemoryTest option to make sure your laptop memory is ok...  The fact that VLC crashes while launching and glitches in movie playback may also be due to a failing memory stick...

---

### Post by olli-sylvanne on 2013-11-05
Thanks for advise. I did this Grub memory test, ok. I don't run or install VLC with memory stick but from net.
I got videos running satisfactorily under Unity, restarted the computer and nothing works. The same as I reported above. And the time runs very fast, again in SMPlayer. Video bad, audio bad.
What creates this instability?
Any ideas?

---

### Post by olli-sylvanne on 2013-11-05
Hello, thanks for help. I think I know the source of the problem. 

The problem:
- might get all running well, but when I restart computer, video goes in slow steps and sound is cracking or no sound, no sync video-audio
- time runs at double speed after computer restart.

The  reason is Rhytmbox. I deleted it and now have SMPlayer + Mplayer2  running in Unity in a consistent way. When I shut down and restart, all  is like I left it. Minor problem with video-audio sync remains. The sync  adjustments at SMPlayer do not help much.
Videos with about 1300*700 .avi run in window in a tolerable way.

My installation: ASUS eeePC 1101ha, Atom processor, 2 GB RAM + Ubuntu 12.04 LTS + Unity. When I switch over to Xfce-desktop, the videos might run slightly faster there.

---

### Post by validust on 2014-01-14
[http://ubuntuforums.org/showthread.php?t=2195959](http://ubuntuforums.org/showthread.php?t=2195959)   :D

---


---
title: "[SOLVED] Sound, but no image in Totem.  Installed codecs already."
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by DayOldPorridge on 2008-01-30
I've already installed the ubuntu-restricted-extras files, but whenever I try to play a movie in Totem, there's still no picture, although there *is* sound.  It's an .avi file, by the way.

And I also tried installing VLC through Synaptic, as well as MPlayer, but I keep getting errors about dependencies that couldn't be installed, so I'm not sure.  Any advice?  Just installed Gutsy last week.  :D

---

### Post by ugm6hr on 2008-01-30
Have you got Compiz on with the latest ATI graphics driver?

If so - this is a known issue.

---

### Post by DayOldPorridge on 2008-01-30
I think so.  Would I need to turn Compiz off or something like that?

---

### Post by ugm6hr on 2008-01-31
If that is the problem - then yes - turn Compiz off and try (No Desktop Effects in Appearance).

There are panel applications that allow you to turn Compiz on and off with one click fr future use.

---

### Post by oedha on 2008-01-31
when i installed mine.......i am not using ubuntu-restricted-extras...
but i am using gstreamer ( 6 of them )
and i also put compiz on.....
now...everything is fine.........my compiz+my vlc can work together.....
mine : intel 915

~E~

---

### Post by DayOldPorridge on 2008-01-31
Hmm.  Well, I have it set to no visual effects, but I'm not exactly sure if I even have Compiz.  :s  How would I find out?  Sorry, I'm really a bit of a noob.  :]

---

### Post by OldGrey on 2008-01-31
Hi, if you installed 7.10 it comes with compiz fusion as part of the package. 

It may be that you need some more codecs to get your videos to play, restricted extras did not do it all for me. If you install the medibuntu repository you can easliy add libdvdcss packages and W32. sounds a bit scary, but if you follow the instructions from the attached its easy peasy.

[https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29)

Good luck.

---

### Post by DayOldPorridge on 2008-01-31
I added the w32 and libdvdcss codecs, but still can't see any picture/image in Totem.

---

### Post by DayOldPorridge on 2008-01-31
Also just installed most of the packages listed in this thread, to no avail:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by LowSky on 2008-01-31
i know you might have tried this...but

add medibuntu repos... follow these instructions (for gutsy only) (cut and paste in terminal)

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
add dvd playback
```
sudo apt-get install libdvdcss2
```.

add codecs (music/movie formats)
```
sudo apt-get install w32codecs
```

now try to play your movie

if that dont work, and it might not, try using VLC or Xine

---

### Post by Rabindranath on 2008-01-31
I had a similar problem long ago. I had a black screen with the audio and when I try to move the window, I was able to see the video while the window was in motion. I dont know why but I got it corrected by changing the desktop effects to "No Desktop Effects". You can change it by right clicking on the desktop and click the "Desktop Effects Tab".

            Try installing all the gstreamer codecs and if it says "unable to download" or something like that, you have to go to 'System > Administration > Software Soources' and ensure that you have checked the multiverse, universe, etc.

---

### Post by DayOldPorridge on 2008-01-31
Nope, still doesn't work; I tried it in VLC, MPlayer, and Totem (using xine-lib).

EDIT: It's set to "No visual effects", and I've downloaded all of the gstreamer codecs already, as well as the libxine codecs.

---

### Post by DayOldPorridge on 2008-01-31
Bump.

---

### Post by RomeReactor on 2008-01-31
Hi. Try [this from UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback")--it's for Feisty, but it might work.

---

### Post by DayOldPorridge on 2008-01-31
Gracias!  It worked/trabajo!  :D  The image in MPlayer is a bit messed up, but atleast it works in Xine.

---


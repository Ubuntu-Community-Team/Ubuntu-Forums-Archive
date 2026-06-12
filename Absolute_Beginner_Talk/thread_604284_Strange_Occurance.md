---
title: "Strange Occurance"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-06
First ignore my 'I think I did something wrong' thread. I just opened up VLC and was able to play a video. But the controls don't work. I can't stop the video, and I close VLC. I don't get it. When I click on the X nothing happens. When I click on close at the bottom of the screen, nothing happens. 

I was able to get rid of all of the medibuntu files that I previously installed, and just installed libdvdcss2. 

Can anyone shed any light on what is going on?

I also had google earth installed and tried to look at it, but it was initializing forever and I couldn't close it either. 

I bet if I tried to run other stuff I would probably run into the same problem.

---

### Post by SpiritIsReality on 2007-11-06
howdy
maybe try 
sudo aptitude -s remove --purge vlc
which will just -s simulate the command.
If it doesn't threaten to do anything drastic, like remove ubuntu-desktop or something,
you could run the command
sudo aptitude remove --purge vlc
then
sudo aptitude install vlc
and see if it works better?
otherwise it could be a video configuration file needing attention, maybe 
sudo dpkg-reconfigure xserver-xorg
trails

---


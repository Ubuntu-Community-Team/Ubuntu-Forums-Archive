---
title: "Yasoumalak's ubuntu problems !!help!!"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by yasoumalaka on 2006-08-17
Hi, just for the record Ubuntu is my favorite distro after trying suse and fedora, but I've having some minor problems here they are:

I can't get the Gstreamer plugin to show up in Amarok. 

Also it seems like Amarok is playing the media, but I hear nothing. Whats wrong???

I had previously set realplayer to automaticly play shoutcast playlist, but nowits giving me errors so I want to change which program that automatically plays these playlist. I've looked everywhere and can't seem to get it changed.

Also I tried formatting my ntfs storage drives to fat 32 is this a good idea for interoprability between windows and linux???

When I did convert them it was a B!@tch- not sure why. And it took less than a minute to format 320GB is that normal??? Let me know if you think I got them formated right and if this is the optimal setup.

 Thank you in advance for any guidance you can provide

---

### Post by =Kevin= on 2006-08-17
Hey Yasoumalak,

you need to install multimedia codecs to hear mp3,play movies etc.
The way to do this is: (type this in terminal)

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install w32codecs


You can also look at [http://www.ubuntuguide.org]("http://www.ubuntuguide.org"), there is much explained there!

Good luck ;)

---


---
title: "No sound for qicktime movies"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by wedshot on 2007-04-17
I finally got ubuntu 6.06 to play quicktime movies form an educational website.  The vidio is fine but I can't get the sound to work.  I know the website works cause my other boxes (Mac 10.4.9) and (xp-pro) work.
What's up?
Wedshot

---

### Post by Rush_898 on 2007-04-17
I know I had problems w/ sound on websites, and not just flash sound until I did this.

Note: if sound doesn't work in Flash Player (for example on YouTube), do the following:

    * Install alsa-oss 

sudo aptitude install alsa-oss

    * Open the firefoxrc file 

    Ubuntu users 

sudo gedit /etc/firefox/firefoxrc

    Kubuntu users 

sudo kate /etc/firefox/firefoxrc

    * Change: 

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

    * Restart Mozilla Firefox. Now sound should work in Flash Player. 



I lifted this from ubuntuguide, it's worth a try

---

### Post by wedshot on 2007-04-18
I followed your suggestion and while the procedure went well, the sound still does't work.  When I open the movie, it opens in gxine.  I wonder if that has anything to do withn it?

---

### Post by Seisen on 2007-04-18
Have you downloaded the multimedia codecs, this might eliminate the problem.  

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")

---

### Post by wedshot on 2007-04-18
Seisen:  This is what the terminal returned;
wedshot@wedshot-desktop:~$ sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "gstreamer0.10-plugins-bad-multiverse"
No candidate version found for libxine-extracodecs
The following packages are BROKEN:
  gstreamer0.10-plugins-ugly-multiverse
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.2kB of archives. After unpacking 106kB will be used.
The following packages have unmet dependencies:
  gstreamer0.10-plugins-ugly-multiverse: Depends: liblame0 (>= 3.96.1-1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
wedshot@wedshot-desktop:~$

---

### Post by Seisen on 2007-04-18
Post your source list.

---

### Post by wedshot on 2007-04-20
I loaded Feisty Fawn and put in all the codeccs you suggested from another problem we talked  about. 
Thanks
Wedshot
(closed)

---


---
title: "Downloading and Installing Mplayer"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Tokpile Quohog on 2008-04-13
Hi. I'm completely new to Ubuntu and I was wondering how to install mplayer. From the site they say I had to download 3 different things but I really have no clue what to do.

Any help is greatly appreciated.

---

### Post by sayakb on 2008-04-13
Open a terminal and type:
```
sudo apt-get install mplayer mplayer-nogui
```
This would provide you the version available through the repositories.

---

### Post by Tokpile Quohog on 2008-04-13
I tried the command but I got this:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
           Depends: libaudio2 but it is not installable
           Depends: libdvdread3 (>= 0.9.6) but it is not installable
           Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: liblzo1 but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
           Depends: libpulse0 but it is not installable
           Depends: libungif4g (>= 4.1.4) but it is not installable
           Depends: libx264-54 but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: libxvmc1 but it is not installable
           Depends: mplayer-skins but it is not installable
           Conflicts: mplayer-nogui but 2:1.0~rc1-0ubuntu13.2+medibuntu1 is to be installed
  mplayer-nogui: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
                 Depends: libaudio2 but it is not installable
                 Depends: libdvdread3 (>= 0.9.6) but it is not installable
                 Depends: libfaac0 (>= 1.24clean) but it is not installable
                 Depends: libggi2 (>= 1:2.2.1) but it is not installable
                 Depends: liblzo1 but it is not installable
                 Depends: libmad0 (>= 0.15.1b) but it is not installable
                 Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
                 Depends: libmpcdec3 but it is not installable
                 Depends: libpulse0 but it is not installable
                 Depends: libungif4g (>= 4.1.4) but it is not installable
                 Depends: libx264-54 but it is not installable
                 Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
                 Depends: libxvmc1 but it is not installable
                 Conflicts: mplayer
E: Broken packages

---


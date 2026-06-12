---
title: "Install missing plug-in for sream videos..."
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-13
Hello, I have installed VLC and Xine-ui for my xubutu desk top, and when I download a video clip and open it in my download manager, the video works. But when I click on a windows media player streaming video link on websites, I get a "install missing plugins" message, then when ever I try to install the missing plugin, it redirects me to the WMP10 11beta page of Windows.

I was just on Surfline's website that has surfing trailers and amateur surf videos, and it needed a certain plug-in.

Does anyone know how I can configure one of my media players to work with it. I also have Real10 and xfmedia.

I would like to do this without using automatix2 or Easyubuntu if possible, since I've been able to configure my desktop so far without either of them.

Thanks again,
-c.

---

### Post by crimesaucer on 2006-10-13
I was just trying to add this for streaming video playback for VLC:

apt-get install avahi-daemon
apt-get install avahi-utils

$ apt-get install avahi-daemon
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
me@me-laptop:~$ apt-get install avahi-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
me@me-laptop:~$

I also added the mozilla firefox VLC plug-ins for my media player and it had some other suggested packages, are these codecs and libraries?:

The following extra packages will be installed:
  libggi2 libgii0 libgii0-target-x libglide2 libsvga1 vlc-plugin-arts
  vlc-plugin-esd vlc-plugin-ggi vlc-plugin-glide vlc-plugin-sdl
  vlc-plugin-svgalib
*****Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 device3dfx-module
  device3dfx-source
Recommended packages:
  libggi-target-x libggi-target glide2-bin*****
The following NEW packages will be installed:

Do I want to add those packages that I stared****?? Should I use synaptic or is there a faster way using terminal? like sudo apt-get install libggi-target-emu libggi-target-monotext libggimisc2 device3dfx-module
  device3dfx-source 

sudo apt-get install libggi-target-x libggi-target glide2-bin

or would I have to install each package seperate like, sudo apt-get install libggi-target-x ?

Thanks.

---

### Post by chuckyp on 2006-10-13
You need the browser plugin to use your movie players.  Like I have mplayerplug-in so firefox can use mplayer to play streams.  You can check which plugins you have installed by going to about: plugins (no space after the :  )   in firefox.

---

### Post by crimesaucer on 2006-10-13
thanks, would you suggest the media player extension to target my VLC and Xine-ui, and also my Real10 and xfmedia?

---

### Post by catlett on 2006-10-13
I just watched a video on surfline. I chose windows media format for my choice of video on their site. I have mplayer as my firefox video player and I have the win32 codecs installed. Do you have mplayer and the win32 codecs? If not do you need the instructions for it?

---

### Post by crimesaucer on 2006-10-13
I have VLC, Xine, Real 10, and xfmedia (default with xfce xubuntu).

I have read that most people like the VLC. I have also read things about mplayer being popular, don't bother about the instructions unless there is something that isn't covered in the terminal code on the ubuntu wiki page or synaptic. Thanks for offering though.

This is the page of instructions I've been following, it is pretty informative: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

I did install the Win32 codecs with the install of the VLC and VLC plug-ins for Firefox.

Surfline rules, huh? 

I love being able to check the waves at all of the places I've surfed and want to surf, I just wish some of their cameras were better.

---


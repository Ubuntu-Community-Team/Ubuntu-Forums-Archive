---
title: "Totem-xine....MPlayer problems."
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by ~zoey~ on 2006-09-08
I have been trying to get streaming video going on some news websites.  I was able to get Totem-xine working, but it stops to buffer about every 10 to 15 seconds, and so far I have not discovered an answer to that problem.

MPlayer gives me 'couldn't resolve name for AF_INET6:video.cgi.cbsnews.com'  I can get it to play using Firefox media player connectivity, but it is very jerky.

I am running Dapper and I have the Win32 codecs installed and also ran this for MPlayer:    sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion and eveything installed OK.

I am totally lost and havenj't a clue as to what I should do next.](*,) :confused: ](*,) 

zoey

---

### Post by Omnios on 2006-09-08
Hi for a while I had a 128kbs connection and it did not play well with streaming video. I have mplayer, totem xine, and realplayer. I also use the media connection extention for firefox but non of this solved my problem. Well one possibllity would be to try to see if you can get the Linux Realplayer working for these as it has a connection network think where you can buffewr the entire clip

---

### Post by gadfly22 on 2006-09-08
Looks like you were trying to use the videos on the CBSNews site.  I had absolutely no luck getting streaming video from there until I started using the Media Connectivity extension on Firefox.  For some reason, the realplay video on CBSNews.com will play nicely with Mplayer (or recently, RealPlayer itself) thru Media Connectivity but not otherwise.  At least that was my experience.

---

### Post by ~zoey~ on 2006-09-08
The only one that I can get to work there at all is Totem-xine and if it didn't have to buffer every 10 to 15 seconds, it would be wonderful.  It is smooth, no jerkiness like I get in MPlayer [when I can get it to go at all!].  I installed Realplayer10, but that didn't help at all.  I wish that I could find an answer to the buffer problem.  The problem is there playlist or streaming video.

Thanks, zoey

---


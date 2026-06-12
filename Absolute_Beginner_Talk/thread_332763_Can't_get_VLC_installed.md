---
title: "Can't get VLC installed"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-06
From this thread: [http://www.ubuntuforums.org/showthread.php?t=323855&highlight=VLC]("http://www.ubuntuforums.org/showthread.php?t=323855&highlight=VLC")
 put in : 
wget [http://downloads.videolan.org/pub/videolan/vlc/0.8.6/vlc-0.8.6.tar.bz2](http://downloads.videolan.org/pub/videolan/vlc/0.8.6/vlc-0.8.6.tar.bz2)
tar xvf vlc-0.8.6.tar.bz2
That works fine.


But when I got two step 2: 
sudo apt-get install libwxgtk2.6-dev libdvbpsi4-dev libmpeg2-4-dev libmpeg3-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev build-essential automake1.9 libtool libx11-dev libdvdread-dev libdvdplay0-dev libdvdnav-dev libdvdcss2 libfaad2-dev libebml-dev libmatroska-dev libmp4v2-dev libpostproc-dev libavformat-dev ffmpeg libavcodec-dev libvcdinfo-dev libdts-dev libslp-dev gettext liblivemedia-dev libsdl1.2-dev libdv4-dev libnotify-dev libcdio-dev libavc1394-dev libcddb2-dev

I get the error message:
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read

Please tell me what I need to do to rectify this. Thank you in advance.:confused:

---

### Post by taurus on 2007-01-06
There is something wrong with the first line of your /etc/apt/sources.list.  If you don't know how to fix it, post it here but you can place a # in front of it to comment it out...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kliljedahl on 2007-01-06
I did that and still get the same message. Here's how the first few lines look now:
#sudo chmod +x ~/.mozilla/plugins/libflashplayer.so
sudo chmod +x /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree flashplayer-nonfree
sudo apt-get update
sudo wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

When I put in: gksudo gedit /etc/apt/sources.list
 I get the message: (gedit:7958): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 and then gedit opens.](*,) ](*,)

---

### Post by taurus on 2007-01-06
Can you please post the complete list of your /etc/apt/sources.list?  It looks to me like it has a bunch of stuff in there that shouldn't be in there...

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by kliljedahl on 2007-01-06
Here's the whole thing as it is now: 

#sudo chmod +x ~/.mozilla/plugins/libflashplayer.so
sudo chmod +x /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree flashplayer-nonfree
sudo apt-get update
sudo wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
kliljedahl@kliljedahl-desktop:~$

---

### Post by taurus on 2007-01-06
Edit /etc/apt/sources.list with (and don't worry about the warning message)

```
gksudo gedit /etc/apt/sources.list
```
and delete all these lines from it...

```

#sudo chmod +x ~/.mozilla/plugins/libflashplayer.so
sudo chmod +x /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree flashplayer-nonfree
sudo apt-get update
sudo wget http://3v1n0.tuxfamily.org/EDD1E155.gpg -O- | sudo apt-key add -

```
Save it and run

```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by kliljedahl on 2007-01-06
Thank you very much, that seemed to work. Now I'll search for that thread to make it default. Your help is greatly appreciated.  I realize I have a huge learning curve here, and I do intend to learn it.

---

### Post by taurus on 2007-01-06
You mean something like

System -> Preferences -> Removable Drives and Media -> Multimedia -> Video DVD Discs?

---

### Post by kliljedahl on 2007-01-07
I guess. Where do I find the VLC file after that?

---

### Post by taurus on 2007-01-07
You mean how would you run vlc after you installed it!

Applications -> Sound & Video -> VLC.

---

### Post by kliljedahl on 2007-01-07
It plays everything but DVDs I'd like to get it as the default for them since Totem always pops up.

---

### Post by kliljedahl on 2007-01-07
It plays everything but DVDs I'd like to get it as the default for them since Totem always pops up.

---

### Post by taurus on 2007-01-07
Did you change it to vlc in System -> Preferences -> Removable Drives & Media -> Multimedia -> Video DVD Discs?

---

### Post by kliljedahl on 2007-01-07
Do I just type vlc, or is there more needed? I apologize for my ignorance, but I do really appreciate your help.

---

### Post by taurus on 2007-01-07
After clicking all those steps, System -> Preferences -> Removable Drives & Media -> Multimedia -> Video DVD Discs, you need to type **vlc** in the C_o_mmand for Video DVD Discs.  I believe right now it has "totem %m".  Make sure the "Play video DVD  discs when inserted" has a check mark in front.  Click Close and see if vlc opens when you pop in a DVD movie!

---

### Post by kliljedahl on 2007-01-07
It installed fine, it plays everything fine except DVDs. I tried the System, Preferences, Removable Drives and Media and typed in vlc. There must be more to the command line than that, as it still won't work.

---

### Post by taurus on 2007-01-07
Have you tried to log out and back in again?

---

### Post by kliljedahl on 2007-01-07
i did that. It opens when I put in the DVD.  Unfortunately it doesn't play. I'll worry about that later. Everything else works just fine. Thank you so much for all your help, I appreciate your patience and kindness.  DVD viewing is not high on my priority list, but it would have been nice as an extra.
	:smile: 	:smile: 	:smile:

---


---
title: "Online Radio problem?"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-02-17
Hi there.  First of all thank you to all those who helped me get Breezy Badger up and running.  See the two threads below :) 

[http://ubuntuforums.org/showthread.php?t=131014](http://ubuntuforums.org/showthread.php?t=131014)

[http://ubuntuforums.org/showthread.php?t=131474](http://ubuntuforums.org/showthread.php?t=131474)

I've managed to get the system to play dvd's mp3's cd's and mpg's which was what was causing me the bulk of my install and running problems.  I've tried using the stand alone RP using the link on the BBC site but it doesn't work.  

I wonder if anyone could help with a RealPlayer problem?  I'm sure there is some small lib file that can sort this out - I hope 

I've downloaded RP 10 from the Real site and followed the instructions on here on what to put into the Terminal Window.  I seem to have got a perfect install but when I try to listen to my favourite radio soap opera ( [http://www.bbc.co.uk/radio4/archers](http://www.bbc.co.uk/radio4/archers)  I get no sound.  RP10 plays mp3's no problem.

I think that it may well be a problem in setting it to recognise the type of stream that the beeb uses to broadcast with.

Has anyone any idea on how to sort this one out.  

Thanks in advanc

---

### Post by patrick295767 on 2006-02-17
you' d have to install realplayer 10 and make it available
(to download it on their official web site (for linux part))
  
and also:
```
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home
apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer
##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  

# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup



##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config
```

---

### Post by KeyboardJockey on 2006-02-17
[QUOTE=patrick295767]you' d have to install realplayer 10 and make it available
(to download it on their official web site (for linux part))
  
and also:
```
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home
apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer
##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  

# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup



##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config
```[/QUOTE]


HI patrick295767 thanks for getting back to me.

I've installed RP10 as per the instructions on here and on the RP site.  I'm still a bit of a nervous Terminal Window user so do I just cut and paste all the code above into the TW?

---

### Post by KeyboardJockey on 2006-02-17
I tried entering this code it appeared to load some stuff on but still no sound from the site.

---

### Post by KeyboardJockey on 2006-02-17
Whoops I must have done something badly wrong here.

Now Rplayer won't open at all now.  How do I remove realplayer from the system so that I can later reinstall.

---

### Post by qwazert on 2006-02-17
When cutting and pasting directions, make sure to enter ONE LINE at a time and to hit ENTER after each command!

---

### Post by KeyboardJockey on 2006-02-17
[QUOTE=qwazert]When cutting and pasting directions, make sure to enter ONE LINE at a time and to hit ENTER after each command![/QUOTE]

Oh.  I think I've made a very newbie mistake.

How do I get out of this one?  I've now got a situation where the Real Player icon is in the Apps menu but it doesn't open as it did before.

I need to remove Real Player and all the associated files.  I can;'t use Add/Remove applications as I get the error message below:

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first"

Is there a Terminal Window command that will allow me to 

a) correct this problem with not being able to get exclusive lock

b) will totally un install realplayer and all associated files?

thanks

---

### Post by qwazert on 2006-02-17
My guess (and remember that I too am a noob to this...) is that you don't necessarily need to UNinstall anything.
Reboot your computer (to KILL all running processes) then run the commands in Terminal again.

If this doesn't work, you might have to use the Synaptic Package Manager to UNinstall everything relating to RP.

But remember...I am a NOOB!

---

### Post by KeyboardJockey on 2006-02-17
[QUOTE=qwazert]My guess (and remember that I too am a noob to this...) is that you don't necessarily need to UNinstall anything.
Reboot your computer (to KILL all running processes) then run the commands in Terminal again.

If this doesn't work, you might have to use the Synaptic Package Manager to UNinstall everything relating to RP.

But remember...I am a NOOB![/QUOTE]


Thanks for that.  Judging by your post date your less of a noob than me but I will bear  that in mind.  I'll try Synaptic.

---

### Post by KeyboardJockey on 2006-02-18
OK this one came courtesy Linux Express Website.  [http://www.linuxgazette.com/node/10824](http://www.linuxgazette.com/node/10824)

It was originally a Terminal Window command to allow listening to the BBC World Service.

The original command was:

/usr/bin/mplayer -cache 256 rtsp://rmlivev8.bbc.net.uk/farm/*/ev7/live24/worldservice/liveinfent.ra

What I did was c+p into an Open Office wordpro document and change the  command to :

/usr/bin/vlc -cache 256 rtsp://rmlivev8.bbc.net.uk/farm/*/ev7/live24/radio4/listenagaininfent.ra

I pasted this (after sudo of course) into the Terminal Window entered my PW and hit return.

I closed the TW when the process had completed and opened up the BBC Radio 4 website  [www.bbc.co.uk/radio4/archers](www.bbc.co.uk/radio4/archers)

My chosen radio programme then opened up with no problem using VLC.

I'm well pleased that this has worked as it is the first time I have modified a given command line with a bit of lateral thinking.  

Thank you all for the help trying to get Real Player working but VLC works far far better now.

Looks like the only reason I will have to go back to XP now is to play Doom :( 

I hope that other newbies who are having problems with online BBC radio read this as it might solve their problem.

:)

---


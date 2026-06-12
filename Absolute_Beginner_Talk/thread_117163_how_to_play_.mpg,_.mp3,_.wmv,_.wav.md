---
title: "how to play .mpg, .mp3, .wmv, .wav"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by russ1625 on 2006-01-14
how do you play .mpg's, .mp3's, .wmv's, .wav's, or any audio video format commonly   used with windows

---

### Post by christhemonkey on 2006-01-14
You need to enable the universe and multiverse repositories, and then get the w32codecs in synaptic or with apt-get.

---

### Post by Mustard on 2006-01-14
[QUOTE=christhemonkey]You need to enable the universe and multiverse repositories, and then get the w32codecs in synaptic or with apt-get.[/QUOTE]

Well not quite. :)

w32codecs isn't in the standard repostories.

I would suggest you read this wiki page on restricted formats....

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

This other link below will give you an idea on how to set up music and movies....

[http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies)

---

### Post by patrick295767 on 2006-01-14
apt-get -f install xmms
  
then  :
```
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home
apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts
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
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer


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
```

---

### Post by christhemonkey on 2006-01-14
[QUOTE=Mustard]Well not quite. :) [/QUOTE]

Lol! my bad :p

---

### Post by Mathias-K on 2006-01-14
Or you could take a look at Automatix --> [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

It's a graphical installer for all bunch of handy programs. It got me up and running with MP3's, MPG's and DivX :)

---

### Post by diggs on 2006-01-14
Am I the only one that finds it odd that in the year 2006 there's an OS that you need to downlad extra programs just to play an mp3 file? Seriously, it's kind of weak, IMO.

Anyways, to the starter of the thread: at the to of this forum there is a thread called about automatix, I suggest you install and run it, it will make your life in linux a lot easier and allow you to avoid typing in such long strings of code-like in the post above.

---

### Post by Perfect Storm on 2006-01-14
[QUOTE=diggs]Am I the only one that finds it odd that in the year 2006 there's an OS that you need to downlad extra programs just to play an mp3 file? Seriously, it's kind of weak, IMO.
[/QUOTE]

Not weak, but free. Ubuntu is free and will stay that way, that's why non-free stuff aren't in the (official) repo or CD.

---

### Post by diggs on 2006-01-14
It's so easy to get you linuz guys on the deffensive ;)

I'm just of the school of thought that simple things that I can do on other operating systems should be simple in others to make them a competitive and viable option, regardless of cost. Given that this OS comes with complex proggies like gimp and such, you'd think that something like playing an mp3 file would be integrated right in. At least there is a reason for it not be.

I just hope that I donut ever have to change the refresh rate on my monitor. I found a thread on it, good god it looked hard.

---

### Post by Mathias-K on 2006-01-14
> **diggs]It's so easy to get you linuz guys on the deffensive  said:**
> 

Understandable. They are software politicians, eager to speak for their course.

[QUOTE=diggs]I'm just of the school of thought (..) you'd think that something like playing an mp3 file would be integrated right in.

I am sure you understand why their take on free software prohibits them from including such formats and codecs. I believe that the only way to make some progress on this matter is to support initiatives such as Automatix.[/QUOTE]

[QUOTE=diggs]I just hope that I donut ever have to change the refresh rate on my monitor. I found a thread on it, good god it looked hard.[/QUOTE]

Agreed. Controlling your hardware is way to hard compared to Windows.

---

### Post by sesstreets on 2006-01-14
This is slowly going off topic so whatever...

I think the thing that graphical linux's are missing is a common installation format. Not exe but something like it, where it will download everything you need, it was the biggest problem i had adjusting to ubuntu,,,no one click installs, and NO synaptic is not a replacement for installers.

zJust my thoughts

---

### Post by meborc on 2006-01-14
that is the linux way... and i believe it is the best way... of course it is different then windows... well... they are 2 different OS'es... linux is an alternative, not substitute... so keep that always in mind when starting to invent the wheel :D ... 

and aren't you happy that you are now virus free??? :)

---

### Post by Mathias-K on 2006-01-14
I'd just be happy if all Linux programs could be installed onto all distros. It's quite frustrating to see all kinds of .deb, RPM and .sh installers floating around..

Yes, i'm happy that i'm virus free, but that does in no way make the installers easier :)

---

### Post by tageiru on 2006-01-14
[QUOTE=diggs]It's so easy to get you linuz guys on the deffensive ;)

I'm just of the school of thought that simple things that I can do on other operating systems should be simple in others to make them a competitive and viable option, regardless of cost. Given that this OS comes with complex proggies like gimp and such, you'd think that something like playing an mp3 file would be integrated right in. At least there is a reason for it not be.[/quote]
Fluendo is working on building plugins for gstreamer that will allow you to play most non-free codecs. You will have to spend hard cash for each codec, but it will at least be legal (depending on where on the planet you live).

---

### Post by christhemonkey on 2006-01-14
where exactly is it illegal to play mp3s?

---

### Post by Mathias-K on 2006-01-15
[QUOTE=christhemonkey]where exactly is it illegal to play mp3s?[/QUOTE]

In some countries, most importantly USA, there are certain patent related issues with releasing Ubuntu with MP3 support out of the box.

---

### Post by christhemonkey on 2006-01-15
ok, thanks for clearing that up.

---


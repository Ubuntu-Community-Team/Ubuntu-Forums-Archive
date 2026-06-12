---
title: "totem"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by robbieatsooke on 2006-01-17
this is my first time on this forum ,ive spent some 50 hrs trying to get my ubuntu to work.Ive had very little success and tons of frustration,ime beggining to think its a freek and its never going to be workable.For instance what is this totem,it dose absaluty nothing,wont play any radio,movies,streemers nomater what i do.I downloaded an avi. movie 2 months ago an todate have not been able to just play the thing.I could say a lot more but ime just to angry,it shouldnt be this way,even the "inferior" windows just  "  dose it ",whats missing here?

---

### Post by xmastree on 2006-01-17
[QUOTE=robbieatsooke]whats missing here?[/QUOTE]In a word, **codecs**.

Read this:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)
to see how to install what you need.

That's for 5.04 but I suspect you have 5.10 so be advised that enabling the extra repositories will be different for you.

I suspect someone else will be along with more up-to-date advice... :rolleyes:

---

### Post by 23meg on 2006-01-17
Does Windows play your movies without installing codecs?

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs)

---

### Post by xmastree on 2006-01-17
Another option:
[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)

---

### Post by patrick295767 on 2006-01-17
apt-get -f install xmms

then :

Code:
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

### Post by patrick295767 on 2006-01-17
[QUOTE=robbieatsooke]this is my first time on this forum ,ive spent some 50 hrs trying to get my ubuntu to work.Ive had very little success and tons of frustration,ime beggining to think its a freek and its never going to be workable.For instance what is this totem,it dose absaluty nothing,wont play any radio,movies,streemers nomater what i do.I downloaded an avi. movie 2 months ago an todate have not been able to just play the thing.I could say a lot more but ime just to angry,it shouldnt be this way,even the "inferior" windows just  "  dose it ",whats missing here?[/QUOTE] 
  
I was thinking same than you, but since now, everthg works much better than windows, more reliable, less difficult to install ...
  
Just matter of knowing it ... Have a look to my previous reply
Also, dont forget the zoom config:
echo "zoom=yes" >> ~/.mplayer/config
  
Greetings, 

Pat'

---

### Post by Edho on 2006-01-17
To xmastree,  or others.
Stupid ihave folowd your advise but did'nt read it's for 5.04.

In Synapic i get errorr mesg about the backportreppo's.

Install is not right.

Wat now?

---

### Post by kaamos on 2006-01-17
You can generate a sources.list (with backports and other things) in here: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Edho on 2006-01-17
Kaamos, ok thanks.

I generated a list... putted in sourcelist.

Synaptic give no more errors.

But there is a huge list of UNinstalled he say's.
Install necessary?

My totemplayer works now with mpeg's.


Thanks

---

### Post by hen3rz on 2006-01-17
> Stupid ihave folowd your advise but did'nt read it's for 5.04.
You can find the latest version here:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

Or in **System > Help**

---

### Post by wolfmaniac on 2006-01-18
instead of gstreamer download totem-xine

totem will play nething

---

### Post by xmastree on 2006-01-18
[QUOTE=Edho]But there is a huge list of UNinstalled he say's.
Install necessary?[/QUOTE]Not necessary at all. It's jsut the list of what's available, should you wish to install it. Take time to look through it, if you see something you might like, install and try it out.


Glad you got totem working eventually (and sorry if I didn't make the warning clear enough....)

---

### Post by diggs on 2006-01-18
[QUOTE=robbieatsooke]this is my first time on this forum ,ive spent some 50 hrs trying to get my ubuntu to work.Ive had very little success and tons of frustration,ime beggining to think its a freek and its never going to be workable.For instance what is this totem,it dose absaluty nothing,wont play any radio,movies,streemers nomater what i do.I downloaded an avi. movie 2 months ago an todate have not been able to just play the thing.I could say a lot more but ime just to angry,it shouldnt be this way,even the "inferior" windows just  "  dose it ",whats missing here?[/QUOTE]
I feel and felt your pain, totem sucks, IMO. 

install and run automatix:
[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)

It will make your life a lot easier. make sure you install all the codecs, VLC and xine media players. it's really easy with a minimum of typing in code. It took me hours to try to figure out how to do things like play an mp3 file or whatever, then I found out all I had to do was install and run aoutomatix, all these nerds were throwing code at me and I was getting pissed off. When I found out about automatix, all the nerds were like "oh yeah, you could have done that, it is cool" and what not....:???: 

Good Luck!

---


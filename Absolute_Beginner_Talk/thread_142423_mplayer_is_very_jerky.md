---
title: "mplayer is very jerky"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Larry Grant on 2006-03-10
Playing video in mplayer in the default Breezy installation of firefox is very jerky for me.  Also I cannot get it to play full screen.  I had been mulling over upgrading firefox and trying to get it to use RealPlayer 10, but I didn't get any response to my questions about that, so now I want to focus on just getting mplayer to be less jerky.  I have a brand new (but cheap) Dell computer (I don't remember the CPU speed, since I got it as a gift and I can't figure out how to detect the speed).  Any advice?

---

### Post by Larry Grant on 2006-03-10
By the way, once I get my computer working well with Ubuntu, I'd like to "upgrade" the "second" computer (used by my wife and kids) to Ubuntu from Windows XP.  However, that will be a non-starter unless I can get Video to work well.

---

### Post by patrick295767 on 2006-03-10
[QUOTE=Larry Grant]Playing video in mplayer in the default Breezy installation of firefox is very jerky for me.  Also I cannot get it to play full screen.  I had been mulling over upgrading firefox and trying to get it to use RealPlayer 10, but I didn't get any response to my questions about that, so now I want to focus on just getting mplayer to be less jerky.  I have a brand new (but cheap) Dell computer (I don't remember the CPU speed, since I got it as a gift and I can't figure out how to detect the speed).  Any advice?[/QUOTE]
  
Hi man, 

Here it comes :
 
1/  Install Linux Breezy 5.10 Minimum (wont work with Hoary)

2/
```

apt-get -f -y install mozilla-firefox 
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home

apt-get -f -y install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs
apt-get -f -y install lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 
apt-get -f -y install gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin 
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
apt-get -f -y install gst-register-0.8

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
apt-get -f -y install kfax
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
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config




######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin       #You could install it in /opt/Realplayer
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
  
3/ 
Make sure you have in the user folder : 
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config

Adn now, full screen works fully !!
  (when u surf, right click on the video, fullscreen)
  (u use rox, ok, preess * on ur avi, enter mplayer -zoom  "$@", and  press F to switch to fullscreen On/off)
   
  
Let me know if you encounter any prob

Patrick

---

### Post by taurus on 2006-03-10
If you don't know the spec of your new Dell, go to Dell's website and look up the model of your machine!!!  Chances are you got one of those crappy onboard integrated video controllers...  Need to know which brand name (Intel!!!) so you can install the right driver for it.

---

### Post by Svictor on 2006-03-10
To find out your cpu specs, ```
cat /proc/cpuinfo 
``` To find out what material you have on board (what graphics card for ex.), ```
lspci
```Check the "VGA compatible controller" (or something like this) entry, and see if you find some specific driver in this forum or on google. 

There is also a firefox extension, that lets you choose the player the browser should use, for each media file (thus, you could use vlc, xine, or the standalone mplayer, instead of the default plugin). It's "Media player Connectivity", either from the mozilla website or from here : [http://membres.lycos.fr/sethnakht/]("http://membres.lycos.fr/sethnakht/") .

---

### Post by Unicast on 2006-03-11
[QUOTE=Svictor]There is also a firefox extension, that lets you choose the player the browser should use, for each media file (thus, you could use vlc, xine, or the standalone mplayer, instead of the default plugin). It's "Media player Connectivity", either from the mozilla website or from here : [http://membres.lycos.fr/sethnakht/]("http://membres.lycos.fr/sethnakht/") .[/QUOTE]
Thank you very much for Media Player Connectivity extension pointer. I've been banging my head off the wall trying to get Firefox to use the realplayer plug-in and not mplayer - brilliant stuff!

I was on the verge of going back to XP just to get smooth streaming media again! I'm more than happy now! \\:D/

---

### Post by jbmalone on 2006-03-11
I would say that the easiest way to get mplayer working with Firefox is to just use the Automatix GUI installer.

---

### Post by brooklynlou on 2006-03-11
I'm in the same boat JB.

I installed the stuff through the automatix installer. The Mplayer plug in is still choppy.

---

### Post by Kimm on 2006-03-11
replacing mplayer-plugin with Realplayer 10 wount do you any good, the linux version of Realplayer doesnt play many formats besides the ones Real make.

Follow this very simple HOWTO for installing a later version of mplayer-plugin than the one found in the repositories (if you havn't allredy)

[http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mplayer-plugin](http://www.ubuntuforums.org/showthread.php?t=75817&highlight=mplayer-plugin)

then open the file ~/.mplayer/config
and add this on a new line:

#vo=xv

That _might_ set you up.

---

### Post by Unicast on 2006-03-11
I'd already been down that route Kimm, and streaming video on the BBC News website was still choppy. No matter what I did I just couldn't get the mplayer plug-in to play the real player streams smoothly - and even more annoying than that was the fact that I couldn't force firefox to use the realplayer plug-in! :evil: 

The Media Player Connectivity extension allows "ME" to choose which program plays the streams! \\:D/

---

### Post by jbmalone on 2006-03-11
I have found that it is only choppy on certain videos.

---

### Post by richieboy on 2006-03-14
try adding rhis line to mplayer.conf:

srate = 48000

get there by typing:
sudo gedit /etc/mplayer/mplayer.conf.

it helped me.
rich

---

### Post by TrendyDark on 2006-03-14
[QUOTE=Svictor]To find out your cpu specs, ```
cat /proc/cpuinfo 
``` To find out what material you have on board (what graphics card for ex.), ```
lspci
```Check the "VGA compatible controller" (or something like this) entry, and see if you find some specific driver in this forum or on google. 

There is also a firefox extension, that lets you choose the player the browser should use, for each media file (thus, you could use vlc, xine, or the standalone mplayer, instead of the default plugin). It's "Media player Connectivity", either from the mozilla website or from here : [http://membres.lycos.fr/sethnakht/]("http://membres.lycos.fr/sethnakht/") .[/QUOTE]

Will VLC work better for most media? I have some problems with mplayer being jumpy as well, but I don't like using real player.

---

### Post by Lary Grant on 2006-03-14
So did making it use RealPlayer help a lot?

---

### Post by Lary Grant on 2006-03-14
Thanks for the info!  Sorry that this is such a long post (I spent almost an hour preparing it!).  Please at least read the last paragraph where my question is :)

Here is what  cat /proc/cpuinfo said:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Celeron(R) CPU 2.53GHz
stepping        : 1
cpu MHz         : 2528.709
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
bogomips        : 4997.12

(sorry for posting the whole file... I don't know what is relevant)

And here is what lspci said about my VGA:
...
0000:00:02.0 VGA compatible controller: Intel Corp. 82865G Integrated Graphics Device (rev 02)
...

I am hesitant to install any drivers until I resolve a few questions:

I found a page for the Intel® 82865G Graphics Controller (Linux option) on the Intel site:
( [http://tinyurl.com/qxqu6](http://tinyurl.com/qxqu6) )

but

- One of the system requirements in the release notes says:

	For 32 bit Linux distributions and kernel versions: 

	SUSE* Linux* Professional 9.2 with kernel 2.6.8-24-default
	SUSE* Linux* Professional 9.2 with kernel 2.6.8-24-smp 
	SUSE* Linux* Professional 9.3 with kernel 2.6.11.4-20a-default
	SUSE* Linux* Professional 9.3 with kernel 2.6.11.4-20a-smp		

which may mean that it will only work on SUSE?

- Its filename Intel-3.4.3006-20051209.i386.tar.gz is completely different from the filename I get when I go to the Dell site and search under my Service Tag, then select Video and Windows XP ( [http://tinyurl.com/7r6a7](http://tinyurl.com/7r6a7) ).  (I have to choose Windows XP or else I won't get any video options).  There it says:

Release Title:	Video: Intel Springdale G Integrated Video, Driver, Windows XP, Multi Language, Dimension DE051, v.6.14.10.4299, A07
Release Date:	09/30/2005
Description:	Intel Graphics Driver 6.14.10.4299

Obviously I can't install Dell's Windows driver, but the fact that (a) Dell's driver title is so different from the one on the Intel site and (b) the Intel notes only mention Suse -- make me worried.  Is it OK to install the Intel driver?

---

### Post by danielph on 2006-04-23
I don't know if this helps, but I had problems with mplayer and jerky video and I solved it by configuring the audio driver alsa for hardware: hw=0.0 within the mplayer settings for audio.

This only solved the problem with the application and not the plugin. It also created another problem in audio control, so not a brilliant solution. 

For plugin config see
See [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)

---

### Post by georgetoon on 2006-05-01
MPlayer plays smoothly for me. But the video image does not fill the screen. if I maximize the window, the video stays the same size.

Totem, on the other hand will play full screen, small screen, maximized, etc.  but the video is choppy. I've looked for control under the preferences menu for each app and cannot find anything to adjust the situation.

---

### Post by georgetoon on 2006-05-02
[QUOTE=jbmalone]I would say that the easiest way to get mplayer working with Firefox is to just use the Automatix GUI installer.[/QUOTE]

I used Automatix to get Mplayer and flash, etc.:)  Worked nicely in getting these apps.:)

Only downside: Mplayer does not play video full screen. it is smooth (as I mentioned in this thread, but does not fill the screen. it stays one size regardless of window size.  Totem plays video and will fill the entire screen.  But the video playback is choppy.  The video starts out playing smoothly. But then, a minute of two into the video, it turns choppy. 

Anyone know how i can fix either or both?

Really enjoying my experience with ubuntu.:)  It's a nice change from KDE.:)  

Again, many thanks to all on this forum for their help and patience with me.:)  It is greatly appreciated.:)

---


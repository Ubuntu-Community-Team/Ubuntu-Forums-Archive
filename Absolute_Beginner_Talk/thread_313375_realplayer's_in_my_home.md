---
title: "realplayer's in my home"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-12-05
I got realplayer off their website for the sake of the firefox plugin, which I'm not sure is working, and I don't think I need it anyway. Can I just delete the folder in home and it'll all be gone?

---

### Post by kakalaky on 2006-12-05
That should take care of it.

---

### Post by crimsontide on 2006-12-05
I would like to know how to get the realplayer plugin for firefox to work.:confused:

---

### Post by kakalaky on 2006-12-05
go to System > Administration > Synaptic Package Manager

Opening this will ask for your password, type it in.  Once the program is open click on Settings > Repositories.  Make sure Main, Universe, and Multiverse are checkedand click OK. Now open a terminal and type this in:

```
sudo apt-get install mplayer mozilla-mplayer
```

This will install mplayer and the firefox plugin for it, which supports real media.

---

### Post by P235 on 2006-12-06
Under Edit>Preferences>Content>File Types how do you change the defaults so that the mplayer plugin will run wma format files and others?

---

### Post by kakalaky on 2006-12-06
I actually have totem-xine using win32 codecs setup to handle wmv.  Setting all this up is fairly easy if you use Automatix2.  You can get it here:

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29")

---

### Post by P235 on 2006-12-06
I did the same with easyubuntu, but I don't seem to be able to enjoy embedded video of quicktime or wmv formats.

---

### Post by kakalaky on 2006-12-06
make sure totem-mozilla and mozille-mplayer are installed and restart firefox if they were not.

---

### Post by P235 on 2006-12-06
I checked, totem-mozilla and mozilla player are installed.  I've restarted Firefox and since I installed both packages the computer has even been shut down a few times.  I still get the 'no video' message in place for embedded quick time and wmv files.

---

### Post by kakalaky on 2006-12-06
try this:

```
sudo apt-get remove mozilla-plugin-vlc
```

Edit:  If it is just giving you a black box with (No Video) in the center this will fix it.

---

### Post by crimsontide on 2006-12-06
None of the above has helped.:(  Im tryin to watch video on this site [http://www.weather.com/multimedia/videoplayer.html?clip=1073&collection=topstory&nav=84&from=gn_six_welcome](http://www.weather.com/multimedia/videoplayer.html?clip=1073&collection=topstory&nav=84&from=gn_six_welcome).
Can anyone help?

---

### Post by P235 on 2006-12-06
I removed mozilla-plugin-vlc.  Now when I try to play .wmv files I receive the following message in a pop-up window:

> Totem could not play 'http://videos.m90.org/videos/Will Ferrell - The Phantom.wmv'.

Could not open location; You may not have permission to open the file.

Sometimes I receive a grey box in place of the embedded video now.

Quicktime does work.

---

### Post by crimsontide on 2006-12-06
Found firefox MediaPlayerConnectivity plugin and it works great.    :D

---

### Post by P235 on 2006-12-06
Where did you find this?  I ran a search for firefox with Synaptic and I couldn't find this plugin.

---

### Post by kakalaky on 2006-12-06
I also use MediaPlayerConnectivity.  You can find it here:

[http://membres.lycos.fr/sethnakht/]("http://membres.lycos.fr/sethnakht/")

---

### Post by P235 on 2006-12-08
The Media Player Connectivity add-on proved to be helpful in some cases; however, mozilla plug-ins should only be installed one at a time in order to work effectively.  I learned this from the Ubuntu Customization Guide here:
[URL="http://www.ubuntuforums.org/showthread.php?t=186792"]
http://www.ubuntuforums.org/showthread.php?t=186792[/URL]

> To be able to play videos in firefox you have three choices. Depending on which websites you visit you will get better results with one or the other. Try one at a time and don't forget to restart firefox :
[quote]Code:

sudo aptitude install mozilla-plugin-vlc 
sudo aptitude install mozilla-mplayer 
sudo aptitude install totem-gstreamer-firefox-pluginProblems with video in firefox ?

-Restart firefox and see whether that helps.
-Save your work and log out gnome (Ubuntu). Now you are back at the login screen. Log in again and see if the problem is solved .
-If this is not about flash and you are still experiencing problems then try a different different "player" (mozilla-plugin-vlc,mozilla-mplayer,totem-gstreamer-firefox-plugin)
-Remember it's depending on the websites you visit which one (mozilla-plugin-vlc,mozilla-mplayer,totem-gstreamer-firefox-plugin) will give the best results.
[/quote]

I hope this answers a few questions out there.  Bookmark the Ubuntu Customization Guide :p

---


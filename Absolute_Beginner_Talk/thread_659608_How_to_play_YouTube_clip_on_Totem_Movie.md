---
title: "How to play YouTube clip on Totem Movie?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by LearningPerson on 2008-01-05
OK, I'm totally new.  Can't watch a song from YouTube on Totem Movie.  Is the right program? Tx.

---

### Post by ubuntu-freak on 2008-01-05
You downloaded it to your comp as a filename.flv yeah? Try MPlayer and/or make sure you have the codecs with silly names like 'really bad' 'ugly' etc. You will find them in synaptic if you search for totem.
 
Nathan

---

### Post by LearningPerson on 2008-01-05
Uh, no.  Just wanted to play it on net.  Before I got your response, I downloaded Qttube.  A dark monitor comes up when I press Play on a site  but no sound.  Says it is transferring or read but nothing happens.  Do I have to download as an .flv file for this.  And is Mplayer, Mozilla Player and where might I get it.  Thanks.

---

### Post by Perfect Storm on 2008-01-06
To play youtube clip you need to install flash.

first
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then you can find it in add/remove

or

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by ubuntu-freak on 2008-01-06
You need to open Synaptic and search for the flash plugin. You should also install sun java 5, which is 3 parts, the plugin, bin, and jre packages. 
If you want firefox to stream video properly you should uninstall the totem mozilla plugins and install the mplayer plugins. Oh make sure you have the actual player installed too. MPlayer is a movie player like totem but supports more formats. You don't need to remove totem the player just the totem mozilla plugins.
 
Nathan
 
Edit: If you haven't enabled extra repos then follow the guide here before you do any of the above [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by ubuntu-freak on 2008-01-06
Just thought I'd share how I got streaming working well with MPlayer. Once you have everything above installed and working you should give this a try:
 
sudo gedit /etc/mplayerplug-in.conf and delete everything listed (back it up if you're worried) and then cut and paste these settings. They improve streaming a great deal with certain sites which have caused problems.

download=1
keep-download=0
cachesize=1024
cache-percent=25
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=0
rtsp-use-tcp=0
rtsp-use-http=0
 
Keep-download is an easy way to save streaming media, just change the value to 1 and it will download to your home directory. For an explaination of what the other settings do check out [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php) 
 
You can add vo= and ao= if you want to change the default video and audio output. Otherwise you don't really need those settings in the list. You can add other settings from the link above if you think they will be useful to you.

Works great for me as outlined above. Only have problems with abcnews.com due to their belief that only Microsoft users matter. No big loss though.
 
Also, make sure you completely remove vlc and totem mozilla plugins as they conflict with mplayer.   

Nathan

---

### Post by LearningPerson on 2008-01-06
Thanks, Nathan and Artificial Intelligence.  I will study your replies carefully.  I only download an old song occasionally someone has uploaded as a video or watch a political thingie on YouTube or Veracifier so do I need to keep Qttube?  It takes up a lot of memory if the download from Terminal was any indication.

Sharon

---

### Post by ubuntu-freak on 2008-01-06
You only need the flash plugin to watch youtube clips in firefox. totem doesn't play them in your browser. Totem, vlc, and mplayer plugins play things like wmv, rm, mov, avi, divx etc. I prefer mplayer that's why I posted my advice above. The only media I can't stream is content from poorly designed sites, such as abcnews.com. 
 
Nathan

---

### Post by LearningPerson on 2008-01-06
Installed Mplayer but not the bads & uglies then was led to a site which advised downloading GsStream which played a cpl sites poorly.  Then installed Sun Java 5.  Sites still asked for Adobe Flash. Finally downloaded to Desktop and do not know how to UNPACK.  I thought it might be Extract but don't know what to do when the window comes up.  Tried a few commands in the Terminal but no luck.  Please advise how to unpack.  Thanks.

---

### Post by metalpancake on 2008-01-06
If you have Automatix installed, you should be able to get the correct codects through that.
Yhat' how I fixed mine. :)

---

### Post by LearningPerson on 2008-01-06
Thanks so much, Nathan, Artificial Intelligence and MetalPancake.  I found the answer on this site:  [http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/](http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/)
dated 12/31/07.  I have Gutsy Gibbon and this worked perfectly.  

Is the command for unpack: "  sudo dpkg -i    " followed by the package name?

---

### Post by ubuntu-freak on 2008-01-06
> **LearningPerson said:**
> Installed Mplayer but not the bads & uglies then was led to a site which advised downloading GsStream which played a cpl sites poorly.  Then installed Sun Java 5.  Sites still asked for Adobe Flash. Finally downloaded to Desktop and do not know how to UNPACK.  I thought it might be Extract but don't know what to do when the window comes up.  Tried a few commands in the Terminal but no luck.  Please advise how to unpack.  Thanks.

Open the terminal and paste sudo apt-get install flashplugin-nonfree
 
Youtube vidoes are flash. If you want to watch other formats then follow the advice I posted earlier.
 
It's worth installing the other plugins but don't forget to use just either totem, mplayer and vlc plugins, don't have all three installed.
 
It's fine to have all three players installed though, just not all the players plugins.
 
I recomend you sudo apt-get remove totem-mozilla and then sudo apt-get install mozilla-mplayer.
 
Then use the settings for the plugin I posted earlier. 
 
Hope that helps. I just wanted to help you watch more than youtube flash videos.
 
Nathan
 
P.S. You don't need to unpack whatever it is you downloaded, you can watch youtube in firefox. Also, you should install the bad and ugly codecs so you can watch and listen to all formats.

---

### Post by ubuntu-freak on 2008-01-07
Hey that didn't work for you did it? The flash plugin is broken in the repo for now that's why.

Download it here [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")

Save it to your home folder, then open the terminal and paste this: 

sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb

Hopefully you will be watching youtube after that :)

Nathan

---

### Post by LearningPerson on 2008-01-08
Hi, Nathan,

I looked here: [http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/](http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore/) and found the same info you gave me.   It works great AND I can get stuff with this program that I couldn't with Adobe under Windows for some reason.  So very happy; thanks a lot; and problem solved.

---

### Post by ubuntu-freak on 2008-01-08
I'm glad you got it working. If you struggle to watch videos on any other site try my MPlayer plugin guide.

Nathan

---


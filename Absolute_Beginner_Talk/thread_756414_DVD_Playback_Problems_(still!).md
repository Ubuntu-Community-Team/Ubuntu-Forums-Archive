---
title: "DVD Playback Problems (still!)"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by guitarthrasher on 2008-04-15
I can't play DVD's!

It's bothering me heavily. I've been working on it for 3 days, and I still can't play any. I can play avi's and Xvid's and all the other "restricted" formats, but I still can't play DVD's.

I've installed the libdvdcss2 and all the other packages that have to do with DVD playback, but it doesn't play in MPlayer or VLC or anything. 


Help will be much appreciated!

---

### Post by Inxsible on 2008-04-15
Does your system recognize the CD DVD drive?

When you insert a DVD, does it automatically mount it and show an icon on the desktop ?

---

### Post by guitarthrasher on 2008-04-15
Yes. It shows it on the desktop. It even tries to play it in Totem.

---

### Post by mgmiller on 2008-04-15
Do you have more than 1 optical drive?  On my system, DVD's will only play on one of my drives, the other one always gives an error message.  The drives are fine otherwise, but for some reason, DVD's will only play on one of them.  This started with Ubuntu 6.06, I think and has carried through all my upgrades till now.

Anyway, just try sticking the disc in the other drive (assuming you have one).

---

### Post by frayalejandro on 2008-04-15
Totem usually doesn´t work well with some kind of DVD&#347;. I also tried Gxine, But VLC is the one that has worked for me.

---

### Post by Sinkingships7 on 2008-04-15
run this in the terminal:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

after that's done, run this code for dvd playback:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by crjackson on 2008-04-15
> **guitarthrasher said:**
> I can't play DVD's!

It's bothering me heavily. I've been working on it for 3 days, and I still can't play any. I can play avi's and Xvid's and all the other "restricted" formats, but I still can't play DVD's.

I've installed the libdvdcss2 and all the other packages that have to do with DVD playback, but it doesn't play in MPlayer or VLC or anything. 


Help will be much appreciated!

Here, try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by sciff90 on 2008-04-16
run synaptic package manager and search for automatix install it it will show up in the sytem tools folder
run it and install the non-free dvd codecs from the codecs and plugins menu

---

### Post by Afkpuz on 2008-04-16
The following method is what some may call overkill, but it will install all the codecs you'll probably ever need and DVD's should play.  Assuming you've installed libdvdcss2.


Open add/remove and search for "gstream"

install EVERYTHING with the word gstreamer in the name and your dvd's should play.  If not, you have missed a step.

---

### Post by Cayitano on 2008-04-16
I went through all the suggestions and I still cannot play a Google video. Youtube will come up and play, but not this video: [http://video.google.com/videoplay?docid=-1554935996026794049](http://video.google.com/videoplay?docid=-1554935996026794049) It is a Google video named Willard Water. I tried other Google videos and downloaded FireFox video extensions and still no-go.

The only suggestion I could not do was the automatix because a Synaptic search came up blank even when I separated auto from matix and even used automatrix.

Now I have mythTV which would not play the DVD I rented or the Willard Water video I downloaded. The rented DVD worked in everything but Totem. Looks like I could save myself a lot of trouble if I ordered that disk from LinuxMCE.

Cayitano :)

---

### Post by mgmiller on 2008-04-16
The willard water video is a flash video.  It plays in my firefox without problems.  If you go to this page:
[http://www.adobe.com/products/flash/about/]("http://www.adobe.com/products/flash/about/")

and look under the phrase "Adobe Flash player is installed" It will give you the version of Flash you are using.  Mine says I have version 9.0.124.0

If yours doesn't say this version number, how did you install flash?
Did you get it by installing the ubuntu-restricted-extras package?  That's how I did it.

---

### Post by guitarthrasher on 2008-04-16
It plays the opening previews, but then it stops when it gets to the menu. 

What's going on?

---

### Post by Promaster91 on 2008-04-16
Try this.
[http://ubuntuforums.org/showthread.php?t=709613](http://ubuntuforums.org/showthread.php?t=709613)

---

### Post by wobbiebobbie on 2008-04-16
I got totem working with this link [http://mixeduperic.com/index.php?option=com_content&task=view&id=67&Itemid=46](http://mixeduperic.com/index.php?option=com_content&task=view&id=67&Itemid=46)

---

### Post by Cayitano on 2008-04-18
Still cannot get Google Videos to play. YouTube yes. Did the Totem Xine thing and the whole nine yards suggested in the links referenced to this thread. Opera won't play the Google Videos either. Installed Flash in Synaptic. Installed video downloader extensions for FireFox. Adobe Web site and Synaptic say I have Flash installed. Suggestions? Cayitano  :popcorn:

---

### Post by bumanie on 2008-04-18
You may have tried this already. If not > sudo apt-get install libdvdread3 
> sudo /usr/share/doc/libdvdread3/install-css.sh>  sudo apt-get install w32codecs>  sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll These should install everything you need. Hope it helps

---

### Post by Cayitano on 2008-04-19
Command Line says all the packages are the latest version as I go through your sequence. The Google Video tries to play by opening a black screen like videos usually do, but  then it flashes back to white and nothing happens. Stumbleupon videos do not work either. Right clicking on the blank white screen afterwards reveals a short menu reading: File, Edit, Movie Control, Help, Toggle Sound, and Quit Gnash. Tonight I discovered Add/Remove Applications in the Applications drop-down menu. I am also trying to get my computer to read the blank JVC DVD disk which I want to copy a Linux Distribution to, but I am ot having any luck so I am wondering if there may be a connection between these two problems before I go to another part of the forum to troubleshoot burning a disk. Cayitano (too bad there is not a smilie with a stiff upper lip):)

---

### Post by mgmiller on 2008-04-19
> File, Edit, Movie Control, Help, Toggle Sound, and Quit Gnash. 

The plot thickens!  You are using gnash, not flash.  I suspect that is why you are having flash player problems.  Look in synaptic for gnash, uninstall it (total uninstall, including configuration files), then look for flashplayer-nonfree and select it for re installation.  

Exit Firefox and then restart it and try the flash sites you are having problems with.

---

### Post by Cayitano on 2008-04-20
> **mgmiller said:**
> The plot thickens!  You are using gnash, not flash.  
Exit Firefox and then restart it and try the flash sites you are having problems with.

Merci Beaucoup!

 Have video running, but no sound in YouTube, Google, MPlayer, Totem crashes, VLC crashes, Ogle crashes,. sound OK  in Xine, Gxine (Window sizing problem) and Kaffiene. Just discovered my CD-ROM will not write DVD-R and apparently won't write DVD+R, but this is another issue. Thanks for your solution once again. My W32codecs, flash-plugin, and libdvdcss2 are up-to-date via medibuntu. Time to balance my chakras! :mrgreen:

Cayitano

---

### Post by mgmiller on 2008-04-20
> Have video running, but no sound in YouTube

That's a start.  When you are watching a flash video are you sure the volume slider is turned up in the player and the mute button is not pressed?

Also, double click your speaker icon in the top panel to bring up the volume controls and make sure the PCM slider is turned up and not muted.

This sound issue seems to be common, especially with hardy and FF 3.  See if any of these suggestions help:

[http://ubuntuforums.org/showthread.php?t=695207&highlight=flash+problem&page=3]("http://ubuntuforums.org/showthread.php?t=695207&highlight=flash+problem&page=3")

> Just discovered my CD-ROM will not write DVD-R and apparently won't write DVD+R, but this is another issue.


I assume it's really a DVD burner.  If it is, as you say, a CD-ROM, then it can't write any kind of DVD or CD for that matter.  A CD-ROM drive is a read only device for CD's.

---

### Post by Cayitano on 2008-04-21
> **mgmiller said:**
> That's a start.  When you are watching a flash video are you sure the volume slider is turned up in the player and the mute button is not pressed?

Also, double click your speaker icon in the top panel to bring up the volume controls and make sure the PCM slider is turned up and not muted.

This sound issue seems to be common, especially with hardy and FF 3. 

[URL="http://ubuntuforums.org/showthread.php?t=695207&highlight=flash+problem&page=3


KhaaL at the top of this link which you provided found the suitable solution.
http://ubuntuforums.org/showthread.php?t=695207&highlight=flash+problem&page=3

I removed all of Pulse Audio. I am not running FF3 and all volume knobs are maxed. I went to ESD. Hardware info is saying I have two OSS sound sequencers and one ALSA sequencer. The Audio Controller is an Intel 82801CA/CAM CA'97 which may be saying it is too old to work with PulseAudio? Nevertheless, Mr. Shuttleworth has been redeemed.   \\:D/   Case closed? So be it. So it is. So be the way.

Cayitano    ):P

---

### Post by mgmiller on 2008-04-21
Glad it worked out.  :mrgreen:

Pulse audio is the "big new thing" in Ubuntu sound management.  It seems to be giving a lot of people problems.  Hopefully, they will sort it out quickly, as it is supposed to be easier to code for and almost all system sounds and other programs will be relying on it in the future.

You may want to make a note to yourself as to what you did to resolve the problem, so you can undo it if you have future sound issues as a result of changing your sound system.

Don't forget to mark this thread solved by using the thread tools just above the first post on this page.


PS.
I always wanted to see the Pacific North West.  It always looks spectacular in movies and TV shows.  Is it really as rainy as they say?

---


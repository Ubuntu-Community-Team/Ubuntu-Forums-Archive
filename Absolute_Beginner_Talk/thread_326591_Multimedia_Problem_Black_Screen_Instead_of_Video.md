---
title: "Multimedia Problem: Black Screen Instead of Video"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by kaemrhynn on 2006-12-27
Greetings all, I have been setting up my Xubuntu Edgy system to play various sound and movie file types.  I have used Automatix2 to install all the media codecs that were available via that system but I have struck a problem.

When I tried to play a WMV file I happened to have on my USB drive as a test, I get the sound but no picture.  From the file header I see that the file is:

ASF 856x480 MS WMV 9 (win32) 1010 kBit/s
130 kBit/s Windows Media Audio v2

I know the file is good, as I tried it on my dads WindowsXP machine and all is fine.  gxine gives me black screen, Totem the same and mplayer gives me:

Fatal error!
Error opening/initialising the selected video_out (-vo) device.

My system is fairly old, AMD 333ish, 256 MB RAM, I810 onboard graphics, so I´m wondering if this is the problem or if I have missed something in my configuration somewhere.

Thanks in advance for any advice/solutions that any of you may have :D

---

### Post by Blogesque on 2006-12-28
Same problem here. I used "EasyUbuntu" to install the various codecs and so forth because I couldn't figure out how to install them any other way, and I get audio but no picture. Once it installed, I just hit CNN.com (which uses WM exclusively) and tried to load one of their videos as a test and got nothing but audio. Before the codecs installed, I would just get an error from totem about no handler for MMS files, so it's progress -- but it's only halfway. 

On a related note, C-Span is frustrating like that too (yes, I'm a news junkie). They use nothing but RealMedia/RTSP and I can't make that site's videos work at all. I installed the RealPlayer 10 based on Helix, and I can run it just fine, but it doesn't play anything. No error message, it just sits there on the (Gnome) desktop and doesn't work.

Is this a problem with proprietary formats in a free environment, or have I just not done something right? I'm a rank beginner with Linux, even though I'm a certified repair tech when it comes to M$ machines. I'm not completely clueless when it comes to computer hardware and software, but I'm a saltwater fish swimming in a freshwater lake at the moment... :-k

---

### Post by kaemrhynn on 2006-12-28
As I understand it there is a licensing issue in some jurisdictions regarding proprietary formats in free software.

For this reason, and my strong support for the Free Software movement I try to use free formats as much as possible.  Unfortunately, it is not always possible :(

---

### Post by Michaelt74 on 2006-12-28
Wish I could help, I've been trying to solve the same problem, with no luck. These forums are fine but they rarely take into first time users into account.

---

### Post by mrphd on 2006-12-28
I would have thought that automatix would have installed the necessary codecs. Can I just ask that you try playing the file with the VLC media player? This is my player of choice and it seems to handle pretty much anything that I throw at it. You can install this by going to applications->add/remove and then just searching for VLC.

Let me know if this works.

---

### Post by mgmiller on 2006-12-28
Here is something to try.  I just used it on cnn.com and it worked perfectly.  
First, install vlc ( search for it in synaptic package manager)
Next install mediaplayerconnectivity for firefox.  Get it here:  [https://addons.mozilla.org/firefox/446/]("https://addons.mozilla.org/firefox/446/")

Finally, after restarting firefox, go to Tools, MediaPlayerConnectivity and select configure.  You will see choices for all kinds of media.  Check the one for windows media and set the path to /usr/bin/vlc  

You will have to click one extra time on the cnn website to get it to play as an extra window pops up with the choices of what you want to play, but when you do, it should work with vlc.

Good Luck...

---

### Post by kaemrhynn on 2006-12-28
Well, I have tried vlc and the plugin for firefox, same thing, sound and no picture.

If anyone has other suggestions I would be most grateful.

---

### Post by Michaelt74 on 2006-12-28
Thanks MG, I tried VLC and it works for me too.

---

### Post by Naci Sey on 2007-01-11
I've a similar problem. Can't play any videos on the Web. Went to the VLC site to download their player but the instructions for download/install don't seem applicable to my situation. 

I've only just installed ubuntu 6.06 (dapper drake). The only media player available is Totem. VLC isn't one of the options in the Add/Remove utility and I don't see in the Synpatic Manager either. 

How do I fix this? How to get MPlayer and VLC installed and available to add to Firefox?

---

### Post by Naci Sey on 2007-01-11
I installed mediaplayerconnectivity for Firefox, per  above advice.

Then I followed the instructions in this [Ubuntu Customization Guide]("http://www.ubuntuforums.org/showthread.php?t=186792") to install VLC. Then I ran the connectivity tool to install VLC to Firefox.

Tested VLC on the Web. Still no video, but in one case (cbc.ca), there was sound.

Couldn't install MPlayer. Terminal couldn't find whatever it needed to do that.

---

### Post by mrphd on 2007-01-11
> **Naci Sey said:**
> I installed mediaplayerconnectivity for Firefox, per  above advice.

Then I followed the instructions in this [Ubuntu Customization Guide]("http://www.ubuntuforums.org/showthread.php?t=186792") to install VLC. Then I ran the connectivity tool to install VLC to Firefox.

Tested VLC on the Web. Still no video, but in one case (cbc.ca), there was sound.

Couldn't install MPlayer. Terminal couldn't find whatever it needed to do that.

You might not have the necessary codecs installed. Open a terminal and paste this into it:

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

Then see if it works.

---

### Post by Naci Sey on 2007-01-11
Tried that and got this result:

[INDENT]Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/INDENT]

---

### Post by pissedoffdude on 2007-01-12
> **kaemrhynn said:**
> Greetings all, I have been setting up my Xubuntu Edgy system to play various sound and movie file types.  I have used Automatix2 to install all the media codecs that were available via that system but I have struck a problem.

When I tried to play a WMV file I happened to have on my USB drive as a test, I get the sound but no picture.  From the file header I see that the file is:

ASF 856x480 MS WMV 9 (win32) 1010 kBit/s
130 kBit/s Windows Media Audio v2

I know the file is good, as I tried it on my dads WindowsXP machine and all is fine.  gxine gives me black screen, Totem the same and mplayer gives me:

Fatal error!
Error opening/initialising the selected video_out (-vo) device.

My system is fairly old, AMD 333ish, 256 MB RAM, I810 onboard graphics, so I´m wondering if this is the problem or if I have missed something in my configuration somewhere.

Thanks in advance for any advice/solutions that any of you may have :D

First lets make sure that you installed all the codecs, take a look at this page [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats").  Now open up mplayer right click go to preferences, then navigate to the video tab, and select the second option.

---

### Post by mrphd on 2007-01-12
> **Naci Sey said:**
> Tried that and got this result:

[INDENT]Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/INDENT]

You need to make sure you have the repositries in sources.list.

```
sudo gedit /etc/apt/sources.list
```

to edit the sources.list file. This tells ubuntu where to look for files. At the end of the file add 

```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

Then type ```
sudo apt-get update
``` and then follow the instructions as in my earlier post.

---


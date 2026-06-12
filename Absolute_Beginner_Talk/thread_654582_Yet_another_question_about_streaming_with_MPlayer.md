---
title: "Yet another question about streaming with MPlayer"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by bob12564 on 2007-12-31
One of the problems we newbies have is that there is so much information on these forums that it's overwhelming and it way over the heads of beginners.

Here's my immediate issue.  I'm trying to view the typical Windows multimedia formats (avi, mpg, DIVX, Quicktime, Real, etc.).  There has been so much coverage of this topic in these forums and a zillion suggested solutions.  I tried Totem which said I needed to download the codecs, which it did very nicely.  I could then play avi and mpg files, it couldn't handle streams and the video quality wasn't great.

The solution I decided to use looked the simplest: Install MPlayer and MPlayer plugin for Firefox which will also install the proper codecs for the various Windows media formats.  Many people on the forums have said that MPlayer can handle just about anything including many streams and I liked the simplicity of letting MPlayer worry about the codecs.

I found the MPlayer packages in the Ubuntu "add/remove" programs list and I installed them.   I was able to locate mpg and avi clips on my hard drive and use the "open with" menu to open with MPlayer and they played immediately.  So simple!  OK, the video was again poor in quality compared to what I see in Windows, but for now I'm happy just to have it working.  Then I went to the Real audio stream of my favorite public radio station and was very happy to see the MPlayer plugin in Firefox handle it perfectly!  I then went to another website that has streams of Real video.  Here's when I got my first problem.  The MPlayer plugin opened and began the stream, but all I get is the audio, no video.  For a second test, I found some Real Video files on my hard drive and tried to "open with" MPlayer.  I got this error:

"Error opening/initializing the selected video _out (-vo) device"

I found this error mentioned in several forums but I'm too much of a newbie to understand the responses.  Can someone explain this error in very simple language without lapsing into too much technical stuff?  My video card is a Matrox G550 which is supported by Ubuntu.  

I appreciate the beginners forum.  Those of us taking Linux for a trial run need a simple and basic understanding of our problems and how to solve them.  Unfortunately, many of the discussions in the other forums get into technical debates of one software package over another without explaining the fundamental cause of the problem in plain English. 

Thanks for your help and patience.

---

### Post by foolsh on 2007-12-31
I use this for video and media files

```
sudo apt-get install gstreamer* vlc*
```

For me vlc handles everthing I need

---

### Post by fiddledd on 2007-12-31
VLC is a good option as it will play anything (I think), but if you just want to fix Real Media there's a Guide to install Real Player on Ubuntu.

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

### Post by Xavieran on 2007-12-31
Totem is crap.

I don't know why they even include it...even when I had all the right plugins...no...
Maybe you should try gxine...that is my favourite...if you have any more questions please post them...(I'm trying to get *thanked*  xD)

---

### Post by htaj on 2008-01-01
> **bob12564 said:**
> 
I found the MPlayer packages in the Ubuntu "add/remove" programs list and I installed them.   I was able to locate mpg and avi clips on my hard drive and use the "open with" menu to open with MPlayer and they played immediately.  So simple!  OK, the video was again poor in quality compared to what I see in Windows, but for now I'm happy just to have it working. 

hi. i too experiences this problem. when i watch online videos with mplayer on firefox, the quality is very blurry and horrendous. i was just wondering if there is a solution to this?
thanks

---

### Post by schms on 2008-01-01
"Error opening/initializing the selected video _out (-vo) device" :

It could be that another program blocks the video device -> close all program
or reboot the system, then try again. Is there a video device setting at all ?


Option 1:

Go mplayer -> Preferences -> Video and choose another driver in  "Available drivers"


Option 2:

[http://ubuntuforums.org/archive/index.php/t-20039.html](http://ubuntuforums.org/archive/index.php/t-20039.html)


Option 3:

What is the content of this file in your home directory ?

~/.mplayer/mplayerplug-in.conf

---

### Post by cherry316316 on 2008-01-02
i installed divx for linux from the divx website, but I am not able to play
the divx for linux as I am not able to locate where the hell it has installed the run file
I only see *.h files (
any of you has tried divx for linux ?

---

### Post by bob12564 on 2008-01-02
I did some more trial and error and discovered that MPlayer wil give the error message on some mpg and avi files and not on others.  I can get properties on the media files when it works.  On the others, properties doesn't give anything.  That makes sense because it can't interpret them.

Because there are zillions of codecs floating around the internet, I am beginning to think that the "VO device" is simply a codec problem and nothing more.  I don't know if there's a solution because I guessing that only the most popular codecs may be supported in Linux.  I also get the 'VO" message trying to open a Real video and that may also be a missing codec.  From what I can understand from other forums and the MPlayer website, MPlayer supports Real media 1 and 2 only.  Most newer files are Real Media 3 and 4.  I bet I need to install Real Player just to get proper codecs for MPlayer to work.

For the person who asked about DivX, I had no problem opening a DivX video using the default MPlayer installation.  

I tried to install the win32 codec package as suggested on an Ubuntu support page.  They didn't seem to have any effect.  For one thing, they installed in a location that was different than the one mentioned in the support document. I don't know if the document has a typo or what.

Another forum mentioned installing the Ubuntu Restricted Extensions to get Real support as well as the other Windows codecs.  That package loads a lot of other stuff as well.  I tried it 3 times and it seemed to hang towards the end of the process.  The log said it was installing Windows fonts.  I know using the Live CD method is much slower than running from a hard disk, but I think giving more than an hour to run is sufficient to conclude it was hanging.  By the way, the Flash plugin is part of this package and it fails.  That's been documented as a known bug.

So to conclude, even getting a basic "internet browsing" system stabilized is a very complicated task for a beginner coming from the Windows world.  I may continue to experiment because I'm stubborn or maybe I'll give up and wait for the next release of Ubuntu.

Thanks for all the replies.

---

### Post by ubuntu-freak on 2008-01-05
Best multimedia how-to or I'll eat my cat
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by bob12564 on 2008-01-14
Nathan,

Thanks.  

I'm no longer using the Live CD and I have now installed Ubuntu on a hard drive.  As part of the install I loaded the Ubuntu-Restricted-Extras which I understood would give me access to the win32 codecs and give me what I needed to play DVDs.

Using Totem Movie player I was now able to view just about all my mpg and avi files except for those which seem to be using Indeo 5.  Indeo 5 does not seem to be supported in the Restricted-Extras package.  I cannot view DVDs either.  All that happens is that a window opens (like "Places") and shows the vob file.  There's an error message that says it can't find a program for the vob file.

I decided to install MPlayer again since I read it might support Indeo 5.  It didn't.  MPlayer wouldn't play DVDs either.  I understand that libdvdread3 is loaded as part of the Restricted-Extras package. and is required for DVD playback.

The MPlayer plugin is working and I can listen to radio streams except for flash streams.  I think that's a whole separate issue and I want to take one problem at a time.  Remember that I'm a newbie (LOL!)

Otherwise playback quality in either Totem or MPlayer seems the same and is generally good quality.  I  removed Totem plugin as you suggested.

I think I'm on the right path but I have a long way to go.  I think there's a codec missing for Indeo 5 and I have to install Real Player to view Real video files.  I don't know what I'm missing for DVD playback.  My DVDs are unencrypted.

Help!

---

### Post by ubuntu-freak on 2008-01-14
Hi Bob
 
Please dont install RealPlayer, you don't need it.
 
Install libdvdcss2 for dvd playback.
 
Please read my updated how-to as it explains a few things and has more info.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
There is a fix for flash (YouTube) also.

Post your results and comments in that thread, thanks.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-14
Install VLC for DVD playback by the way. Just not the mozilla-plugin-vlc 
 
Nathan

---


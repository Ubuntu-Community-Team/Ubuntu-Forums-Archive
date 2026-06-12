---
title: "Argh, tarballs are confusing ..."
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by newagelink on 2006-07-14
I downloaded LastfmLinux-1.1.4.tar.bz2, and now am trying to install it.

Before Ubuntu, I used Mandrivalinux 2006 (and before that, the 2005 Limited Edition.) ... Ubuntu is much nicer (and automatically configured my wireless internet! :D Something I couldn't do, which Mandriva couldn't automatically do, either.)

So, since I used Mandrivalinux, I tried to find help there, and followed their sticky guide, [SI-01: How do I install tar.gz's and RPM's?]("http://mandrivausers.org/index.php?showtopic=10615") ... except what they told me to do rarely worked, and almost always turned up errors. Usually at the "make" (no make command configured), "make install", or whatever ... I probably was entering them incorrectly.](*,) 

Now, I'm using Ubuntu's Desktop Guide, which is much more concise! [Installing a Single Package File]("https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html") ... except for tarballs: > you can use the command line to install or uninstall the Tarball file by following the instructions that come with the package.Is each tarball packaged differently? I guess I'm heading back to the last.fm site to see if they give instructions that I missed.

It also doesn't say what to do with .bins, such as "GoogleEarthLinux.bin" ... :???: 

I hate being a newbie; I practically need things spelled out for me at this point. I'm still reading the manual, though ...

---

### Post by T700 on 2006-07-14
See the How to Install Anything link in my sig.

Paul

---

### Post by x64Jimbo on 2006-07-14
You know, the general attitude of most tech-oriented people is that they don't need to read the manual, but when it comes to Linux, you can learn so much more by doing so. I used to skip the manual and find out the hard way, but I have found that every time I read a manual, I find a feature of a program that I didn't know about, or a better way to do things. It very often saves the experts the trouble of answering my questions, and learning it myself actually makes it stick in my head better. While I never read the manuals of things like VCRs, TVs, Laptops, and other hardware, software is often a completely different story, especially Linux.

---

### Post by MrHorus on 2006-07-14
Okay:

```
bunzip2 LastfmLinux-1.1.4.tar.bz2
```
This will unzip the archive and leave you with LastfmLinux-1.1.4.tar in a directory.

```
tar -xvf LastfmLinux-1.1.4.tar
```
You will then untar the archive and have to compile it.

```
cd LastfmLinux-1.1.4
./confgure
make
make install
```

Prefix make install with 'sudo' if your system is set up for sudo.

---

### Post by mostwanted on 2006-07-14
The Last.fm player tarball is precompiled. There should be an executable inside the tarball ready for use, it's not supposed to be compiled, just untared.

But don't you know that a much better alternative exists for Gnome? It's called last-exit and uses Gtk+.

[http://ubuntuforums.org/showthread.php?t=212828](http://ubuntuforums.org/showthread.php?t=212828)

---

### Post by newagelink on 2006-07-14
Thanks for all the replies; I'm doing homework right now, but I'm gonna check out the How to install ANYTHING URL soon & also reply to all the other posts ...
> **mostwanted said:**
> The Last.fm player tarball is precompiled. There should be an executable inside the tarball ready for use, it's not supposed to be compiled, just untared.Yeah, that's why I'm confused. I right click > Extract here, and then I cut and pasted the directory to "/home/daniel/Programs/Last.fm-1.1.4", and in that directory is an executable, "player." I double click that, and everything seems to work great, and I'm like, "Alright! Now how do I add this to Sound & Video ..."

Then I try to play a station, and it automatically closes.
> **mostwanted said:**
> But don't you know that a much better alternative exists for Gnome? It's called last-exit and uses Gtk+.

[http://ubuntuforums.org/showthread.php?t=212828](http://ubuntuforums.org/showthread.php?t=212828)Why is it better? It says it's playing a station, but no audio is coming out. (But my sound is working, because pandora.com works.)

---

### Post by mostwanted on 2006-07-14
> **newagelink said:**
> Thanks for all the replies; I'm doing homework right now, but I'm gonna check out the How to install ANYTHING URL soon & also reply to all the other posts ...
Yeah, that's why I'm confused. I right click > Extract here, and then I cut and pasted the directory to "/home/daniel/Programs/Last.fm-1.1.4", and in that directory is an executable, "player." I double click that, and everything seems to work great, and I'm like, "Alright! Now how do I add this to Sound & Video ..."

Then I try to play a station, and it automatically closes.
Why is it better? It says it's playing a station, but no audio is coming out. (But my sound is working, because pandora.com works.)

It's better because it's Gtk+ and thus integrates with your theme :)

I'm not sure why it doesn't work for you, did you install the deb?

---

### Post by newagelink on 2006-07-14
> **mostwanted said:**
> It's better because it's Gtk+ and thus integrates with your theme :)Oh, cool... (wonders what GTK+ is.)
> **mostwanted said:**
> I'm not sure why it doesn't work for you, did you install the deb?Yeah, I installed the deb that was linked to from the first post (and in so doing, actually wondered if I should or even could scan it for viruses beforehand -- as I automatically do with every file I download in Windows, even if I trust the source. ... which then made me wonder, once Linux becomes more popular, will viruses begin to appear for Linux?)

---

### Post by Third Thoughts on 2006-07-15
> **newagelink said:**
> 
Then I try to play a station, and it automatically closes.


I'll bet this has to do with ALSA support issues. Run the player from the command line. To do that go into the directory you've got it in and type ```
./player
```
Try to play, my guess is that you'll get some sort of seg fault error. Then open the player up again and click the wrench thingy. Change the sound-engine to OSS and see if it'll play that way. That's what I had to do on my system.

~Andrew s.

---

### Post by newagelink on 2006-07-15
You were completely right ...
> **Third Thoughts said:**
> I'll bet this has to do with ALSA support issues. ... Run the player from the command line. ... my guess is that you'll get some sort of seg fault error.Yep. ```
Changing station!
Using ALSA!
Supports 32 bit
Supports 16 bit

RtApi: no devices found for given stream parameters:
    RtApiAlsa: error setting sample rate (44100) on device (hw:I82801DBICH4,0): Invalid argument.
    RtApiAlsa: pcm device (hw:I82801DBICH4,1) won't open: No such file or direct ory.
    RtApiAlsa: pcm device (hw:I82801DBICH4,2) won't open: No such file or direct ory.
    RtApiAlsa: pcm device (hw:I82801DBICH4,3) won't open: No such file or direct ory.
    RtApiAlsa: error setting sample rate (44100) on device (hw:I82801DBICH4,4): Invalid argument.
    RtApiAlsa: pcm device (hw:Camera,0) won't open: No such file or directory.


Segmentation fault
```> **Third Thoughts said:**
> Then open the player up again and click the wrench thingy. Change the sound-engine to OSS and see if it'll play that way. That's what I had to do on my system.I did, and it works. ```
Using OSS!
Supports 32 bit
Supports 16 bit
Playback starting!
New song detected!
Retrieving MetaData!
static.last.fm/coverart/130x130/1165.jpg
Cover returned!
Setting cover!
Buffer empty!
```:) Thanks, Andrew!

(wonders what buffering does, exactly.)

---

### Post by x64Jimbo on 2006-07-17
You mentioned Pandora, so I thought I would plug a little app that I've been following recently. It's called Pandora's Jar and it allows you to save your Pandora stream for later listening, just as you can Tivo your TV shows. For more info, visit the forums at Hak5.org. There's a sticky thread for it.

---

### Post by macogw on 2006-07-17
> **x64Jimbo said:**
> You know, the general attitude of most tech-oriented people is that they don't need to read the manual, but when it comes to Linux, you can learn so much more by doing so. I used to skip the manual and find out the hard way, but I have found that every time I read a manual, I find a feature of a program that I didn't know about, or a better way to do things. It very often saves the experts the trouble of answering my questions, and learning it myself actually makes it stick in my head better. While I never read the manuals of things like VCRs, TVs, Laptops, and other hardware, software is often a completely different story, especially Linux.
I still can't figure out how to make a DVD player, VCR, digital cable thingy and tv all work together.  That's why I get the tv with the DVD player built in and don't use cable.

---

### Post by newagelink on 2006-11-22
Wow, mac. That sucks. :(

---

### Post by aysiu on 2006-11-22
Is LastFMLinux any different from LastFM?

LastFM is available in the repositories, much easier to install than from a .tar.gz

If you have no idea what I'm talking about, you need to read one of these two links:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by newagelink on 2006-11-26
The Last.FM software I was talking about having downloaded (that .tar.bz2 file or whatever) is available at [http://www.last.fm/tools/downloads/](http://www.last.fm/tools/downloads/) "It&#8217;s version 1.0.0 Beta, a 5Mb tar/bzip2 binary package." they say.

I'm looking in my Add/Remove Applications window, with "Show unsupported applications" and "Show commercial applications" both checked, and it's not there when Search: "Last", nor do I see it under the L's when viewing All or Sound & Video.

I'll read those sites (thanks!); maybe I need to add something to my Synaptic Package Manager so it'll show up in the Add/Remove Applications window.

---

### Post by newagelink on 2006-11-26
I don't see it as a package in the Synaptic Package Manager either; it goes from larswm to latd. No 'last'.

I hope to upgrade to 6.10 soon, though, as soon as I can either 1) solve my upgrading problems from 6.06 or 2) backup all my important data and erase the partitions and reinstall completely. Except then I'll have to readd my gaim accounts, reconfigure Thunderbird, etc.

---

### Post by aysiu on 2006-11-26
Sorry. I'm using Edgy, and I just realized [it's not available for Dapper](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lastfm&searchon=name&subword=1&version=all&release=all).

---


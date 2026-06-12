---
title: "Mp3"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Niloc on 2006-08-20
I have a bunch of MP3 files on my Win Box I want to play under Ubuntu. Any suggestions for a downloadable program to do this?

---

### Post by H.E. Pennypacker on 2006-08-20
What exactly are you trying to do and why can't you play them at this moment?  

If you mean you want to transfer the files from your Windows partition to your Ubuntu partition, simply go to "Computer" and copy and paste all those files.  After that, start Windows, and delete them from your Windows partition.  Ensure everything went fine before deleting the originals.

I am not sure what you mean by "downloadable program."  A thorough post is always better than a one line non-descriptive post.

---

### Post by nanotube on 2006-08-20
> **Niloc said:**
> I have a bunch of MP3 files on my Win Box I want to play under Ubuntu. Any suggestions for a downloadable program to do this?

```
sudo aptitude update
sudo aptitude install xmms
```

run these two commands. first one will get the latest package info, second one will install xmms. xmms is kind of a winamp clone for linux. should get you going.

---

### Post by Niloc on 2006-08-20
I can't play them because when I right click on an MP3 file, the only offering I get is 'Rhythmbox Music Player' and when I click on that, I get a screen which says 'Not Playing' so I assumed that Ubuntu does not come with an MP3 player built in...
So I was asking for an application which will allow me to play MP3 files....

---

### Post by Niloc on 2006-08-20
Nanotube, thanks but that assumes I am on the internet, I do not have a connection on the Linux machine, only on a Windows computer.
So when I run your commands I get nothing. When I make it to a computer shop to buy a network modem the first thing I will do is 'sudo aptitude update'.

Why does everything, this forum included, assume everyone has a permanent internet connection, its like assuming everyone has a reliable, available car....  some people don't....

---

### Post by akniss on 2006-08-20
> **Niloc said:**
> Nanotube, thanks but that assumes I am on the internet, I do not have a connection on the Linux machine, only on a Windows computer.
So when I run your commands I get nothing. When I make it to a computer shop to buy a network modem the first thing I will do is 'sudo aptitude update'.

Why does everything, this forum included, assume everyone has a permanent internet connection, its like assuming everyone has a reliable, available car....  some people don't....

I suppose that the assumption is made because you are on the internet right now posting at the forum.  If you need information for getting packages offline, that should be stated in your post.  It is much more difficult to do things that way, and most of us don't have the expertise to help on those matters.  I had a similar issue when I was getting ubuntu installed on an old computer, and it is infinitely more complicated to install packages without an internet connection.

---

### Post by Delkster on 2006-08-20
> **Niloc said:**
> I can't play them because when I right click on an MP3 file, the only offering I get is 'Rhythmbox Music Player' and when I click on that, I get a screen which says 'Not Playing' so I assumed that Ubuntu does not come with an MP3 player built in...
So I was asking for an application which will allow me to play MP3 files....

Rhythmbox, as well as many other media players on Linux, will support several audio and video formats provided that the required codecs are installed.

In order to play MP3 in Rhythmbox, go to **Applications** > **Add/Remove** and search for "codec". Install GStreamer extra plugins (while you're at it, you could also install the GStreamer ffmpeg plugin and Xine extra plugins).

When you try to install them you'll be asked whether you want to enable the 'universe' software repository. The extra codecs aren't officially supported and are thus in the universe repository.

Check out [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for more information.

---

### Post by meng on 2006-08-20
> **Niloc said:**
> Why does everything, this forum included, assume everyone has a permanent internet connection, its like assuming everyone has a reliable, available car....  some people don't....
Because it's a fair assumption to make unless the poster says otherwise!
I'm not meaning to be nasty, all I'm trying to say here is that more information from you means more useful help from us!

---

### Post by Niloc on 2006-08-20
Sorry about that, I am sitting here up here the Burmese border in Thailand with a fairly slow USB connection to my old Win 2000 machine with the IBM T21 laptop sitting next to it. If I can make it to Chiang Mai (two days down and back) I will get an ADSL router which will allow me to connect the laptop to the internet. Meanwhile everything goes via the memorystick, Win-Linux.

---

### Post by pixiemb on 2006-08-20
that was funny ... the most recent topic is just what I wanted to know.. unfortunately the info provided didnt help me :confused::rolleyes:

I went to add/remove but there wasnt a GStreamer available to download. I have clicked on the link that was provided and will keep looking ... I too have mega mp3s and wmv etc which I need to convert.. also .cda I am having probs playing also 

btw ... No we dont all have internet automatically. well I do but then Im not moving and so can commit to an internet plan. life is quite different for some of us, especially when you live in the bush :) where I can assure you very few people around here have internet.

---

### Post by pixiemb on 2006-08-21
i found totem gstreamer and it is already installed. still coulnt play mp3s though... have marked it for reinstallation and will keep going from there.. any help is gladly welcomed ... even if to tell me im a dill and it is easy lol

---

### Post by nanotube on 2006-08-22
you need the gstreamer0.10-ffmpeg package
i bet you don't have that one installed.

to get it installed "offline", you can get the .deb archive here:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fg%2Fgstreamer0.10-ffmpeg%2Fgstreamer0.10-ffmpeg_0.10.1-0ubuntu2_i386.deb&md5sum=a313634655649d7ec505ee54b3095b10&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fg%2Fgstreamer0.10-ffmpeg%2Fgstreamer0.10-ffmpeg_0.10.1-0ubuntu2_i386.deb&md5sum=a313634655649d7ec505ee54b3095b10&arch=i386&type=main)

(in general, to get your packages, for example if this one needs some dependencies, you can get them "manually" from packages.ubuntu.com)
so get that .deb, move it over with your usb stick, and install by doubleclicking, or from commandline with "sudo dpkg -i packagename.deb"

---

### Post by chinaski on 2006-08-22
> **pixiemb said:**
> <snip>

I went to add/remove but there wasnt a GStreamer available to download. I have clicked on the link that was provided and will keep looking ... I too have mega mp3s and wmv etc which I need to convert.. also .cda I am having probs playing also 


there is a very good guide *inside *Ubuntu

from top menu -> System -> Help -> System Documentation

then chose -> Ubuntu Desktop Guide -> Common Tasks -> Multimedia Codecs

there you have info on how to install codecs and a link to the restricted formats page (like mp3, wmv) and also flash, java and other stuff

all installation processes are quite easy to follow and consist in some copy&paste into Synaptic and terminal

p.s. if you have no internet connection on your Ubuntu machine you can manually download packages from [here]("http://packages.ubuntu.com/")

---


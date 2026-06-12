---
title: "XMMS n Beep media player freezes"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by acrylamid on 2005-06-18
Hello.
I got problem with XMMS and Beeo media player.
Both players freezes when I try to listen to a .mp3-file and I must kill the program.

Any idea why?

I followed the "http://www.ubuntuguide.org/#xmms" -guide.
but there was some problem to download all the multimedia codecs. Some of them didn't exist any longer and some other there was some problem with.

I can play music with the "Musicplayer" (Deufult Ubuntu music player I think) But really don't like the program.


My second problem is about AudioScrobbler. ([www.audioscrobbler.com](www.audioscrobbler.com)) I want to use the plugin, I downloaded it and so. The problem begin when i type ./configure
it's some problem about a C. A person i tried to help me said that i needed to intall GCC. Is that correct? Is there any guide out there, GCC looks real difficult to install.

Thanks in advance.

---

### Post by DrMoxie on 2005-06-18
I had the same problem that you describe and the fix that worked for me was to check my sound settings (System-->Preferences-->Multimedia Systems Selector) and ensure that ESD was set in both locations and that the sound test worked.

For the Audioscrobbler plugin, the easiest way to get it installed is to jot down all the requirements and then using the Synaptic Package Manager (System-->Administration-->Synaptic Package Manager) to install it.  That's the route I took to get it up and running and it worked like a charm.

Let us know how it goes!

---

### Post by Mez on 2005-06-18
[QUOTE=acrylamid]Hello.
I got problem with XMMS and Beeo media player.
Both players freezes when I try to listen to a .mp3-file and I must kill the program.

Any idea why?

I followed the "http://www.ubuntuguide.org/#xmms" -guide.
but there was some problem to download all the multimedia codecs. Some of them didn't exist any longer and some other there was some problem with.

I can play music with the "Musicplayer" (Deufult Ubuntu music player I think) But really don't like the program.


My second problem is about AudioScrobbler. ([www.audioscrobbler.com](www.audioscrobbler.com)) I want to use the plugin, I downloaded it and so. The problem begin when i type ./configure
it's some problem about a C. A person i tried to help me said that i needed to intall GCC. Is that correct? Is there any guide out there, GCC looks real difficult to install.

Thanks in advance.[/QUOTE]
 Check whether xmms is using the "eSound" output plugin, or ti will crash (do this before you start trying to play any music)

---

### Post by acrylamid on 2005-06-18
I changed module to eSound and now I can play music.
I also changed the "Multimedia Systems Selector" so I got ESD on both. But the "standardsource" aren't working. Dont hear a sound whatever I choose, the same about the "video-selection" in "MSS".

Thanks a lot!!!



But I find another problem. My cataloge-structure look like this

Music > Rock
          > Pop
          > Electronica
(etc..)

When I choose "file" in XMMS and goes to the music cataloge I see .mp3-files from the Pop-directory (about three cataloges of 30) in the left menu. And then i go into the rock-cataloge and say I choose the cataloge "System of a Down" in the left menu I know see first the system-of-a-down .mp3s and the "pop"-files. There is no problem with Ubuntus "Mediaplayer" and no problem if I choose "dir" in xmms.

The Hdd is a NTFS-system I used when I got Windows XP.



I can't find the audioscrobbler plugin in Synaptic PM. I search for audioscrobbler, scrobbler in name and desciption. Is there any way to force "SPM" to find it? (I mean, I know where on the Internet/www where it is) :D

---

### Post by DrMoxie on 2005-06-19
[QUOTE=acrylamid]I can't find the audioscrobbler plugin in Synaptic PM. I search for audioscrobbler, scrobbler in name and desciption. Is there any way to force "SPM" to find it? (I mean, I know where on the Internet/www where it is) :D[/QUOTE]

Well, the scrobbler piece you'll still need to compile but all of the dependencies like GCC and G++ can be had through Synaptic.  The easiest way to do this is to run the configure for scrobbler (at the command line navigate to where you unzipped scrobbler and type ./configure) and each time it fails on a dependency search for it and install it using Synaptic.  You'll need to do this until it passes the configure with not failures then you can do the make/install.  This is how I got it installed.

As for playing files from an NTFS drive, I have not had any luck.  The most that I can do is browse the directory, write to it, and open the occasional text file.  I have not been able to play any media files from my old XP box but it could just be me and how I set up the network.  I'm working towards migrating all my media files to a Linux box so I can retire that machine.  ;-)

---

### Post by acrylamid on 2005-06-19
[QUOTE=DrMoxie]Well, the scrobbler piece you'll still need to compile but all of the dependencies like GCC and G++ can be had through Synaptic.  The easiest way to do this is to run the configure for scrobbler (at the command line navigate to where you unzipped scrobbler and type ./configure) and each time it fails on a dependency search for it and install it using Synaptic.  You'll need to do this until it passes the configure with not failures then you can do the make/install.  This is how I got it installed.

As for playing files from an NTFS drive, I have not had any luck.  The most that I can do is browse the directory, write to it, and open the occasional text file.  I have not been able to play any media files from my old XP box but it could just be me and how I set up the network.  I'm working towards migrating all my media files to a Linux box so I can retire that machine.  ;-)[/QUOTE]
 okay, Now the AS-plugins works to!
But i didn't do the difficult GCC installure..

a friend give me the tip to download a .deb file instead.
Here it is!
[http://www.sommitrealweird.co.uk/ubuntu/dists/hoary/scrobbler/binary-i386/](http://www.sommitrealweird.co.uk/ubuntu/dists/hoary/scrobbler/binary-i386/)

---

### Post by DrMoxie on 2005-06-20
That's great!  Thanks for the link to the .deb file as well, sure is a timesaver.  :smile:

---

### Post by Unrivaled on 2005-06-23
Hey guys!
I'm using Nforce onboard sound, and I have the same problem where I can only use the Enlightenment Sound Daemon, which is Esound and ESD.
The problem is, some programs default to OSS or ALSA and I can't change them. Is there a way to get them to default to ESD, or remove ALSA and OSS?
Thanks!

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Unrivaled]Hey guys!
I'm using Nforce onboard sound, and I have the same problem where I can only use the Enlightenment Sound Daemon, which is Esound and ESD.
The problem is, some programs default to OSS or ALSA and I can't change them. Is there a way to get them to default to ESD, or remove ALSA and OSS?
Thanks![/QUOTE]

What I do is kill esd when I want to use those programs-

> killall esd

you are currently experiancing the biggest problem with Ubuntu as it is, that THE thing that will be fixed in Breezy. ESD sucks.

---

### Post by Unrivaled on 2005-06-26
Thanks bud, and I actually found a post on how to get rid of ESD altogether. Only took 4 hours of searching :S
[http://ubuntuforums.org/showthread.php?t=30076](http://ubuntuforums.org/showthread.php?t=30076)

Worked like a charm :)

---

### Post by Sionide on 2005-06-26
Hooray! The combination of the eSound thing or the Multimedia Systems Selector fixed my xmms! I also reinstalled it just to make sure...

Thanks a lot!

edit:

```
apt-get install gxmms
```

mmmm, enjoy xmms on the panel :)

---


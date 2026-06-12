---
title: "Rhythmbox in Xubuntu 7.04 on G3 ibook"
date: 2008-02-08
forum: Apple PPC Users
---

### Post by employeeno5 on 2008-02-08
I've refurbished an old iBook out of left-over parts from several "broken" ones.


ibook snow 12"
500mghz
500mb ram
cd/dvd drive
30GB harddrive
airport card

I have a friend who's poor these days and without a computer so I'm going to send this one to her. Despite having explained it's limitations on the PPC architecture (and having a copy of OS X 10.3 around), she's insisting on using a Linux distro.  I'm happy to accommodate her on that as I've become quite a fan of the open source movement.

I've installed Xubuntu 7.04 for PPC. I've got just about everything working well and at this point. I downloaded Rhythmbox for a music player. Music management is going to be an essential for her. Rhythmbox doesn't have many frills but it's simple, straightforward and reliable in my experience so guessed it was a good choice for such a slow computer.

I've installed the restricted format support successfully as far as I can tell. I can play DVDs and have tested mp3 playback in VLC. All of my the music that will be on this machine will end up being in either unprotected .mp3 or unprotected  .m4a format. I've had no trouble getting Rhythmbox to play those formats in my personal Installation of Ubuntu 7.10 on my Dell.
Like I said, I tested .mp3 playback as functioning in VLC and .m4a is playing also in VLC but with distortion.

However,
When I try to play any music file in Rythmbox, it crashes. ' Just shuts right down almost instantaneously. 
This includes .ogg files, mp3s and aac formats. I'm realizing now it would probably be helpful for me have some command line output, but I'm at work at the moment and will post some back later.
In the meantime I have a few questions:

-Does this computer's hardware sound too slow to play mp3s with Rhythmbox?
  If so can anyone recommend a leaner player that still has a jukebox-like interface (some sort of listing of all music files).

-Are there any packages I should be looking for to ensure Rythmbox running correctly?

-If this sounds like a hardware issue, is there anyway to do a virtual work around?

-Anyone know what I can do to improve .m4a playback?

I've seen lots of threads of regarding people putting Xubuntu on old apple machines, so I'm hoping this is something that can be done and that my problems have been encountered before. 
Any help and advice would be hugely appreciated. Once I get music moving okay on this it's going to make wonderful person very happy. She's fairly isolated from the outside world on Prince Edward Island right now, and some music and email would do her well.

Many many thanks.

---

### Post by stream303 on 2008-02-08
> **employeeno5 said:**
> Like I said, I tested .mp3 playback as functioning in VLC and .m4a is playing also in VLC but with distortion.

Have you tried turning down the sound output level in VLC's preferences itself?  On many machines, I've had to knock it back down from 256 to 100, and then readjust the main system volume up a little bit.

> When I try to play any music file in Rythmbox, it crashes. ' Just shuts right down almost instantaneously.

I've also found Rythmbox problematic and stick to VLC or the default Totem Movie Player.  When playing audio files with Movie Player, I go into the preferences and turn off "show visual effects when an audio file is played", just to save on cpu usage.  Just right click on an audio file, and choose which player you want to "open with".

BTW, what a nice friend to be setting up this machine for her!

---

### Post by employeeno5 on 2008-02-08
Thank you for the suggestions. I'll have to try the volume later.

I thought I might have to go with just using a media player vs. a proper jukebox. I'm going to try a couple others before I leave it to vlc.

 
Meanwhile this is what we see when we run things in the terminal.

```
rachel@floppysforever:~$ rhythmbox
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd; not found

```

Then the program opened
I double clicked an mp3 file in the library and then it promptly disappeared leaving only the following out put.

```

(rhythmbox:5612): Rhythmbox-WARNING **: Couldn't find an x overlay
Segmentation fault (core dumped)
rachel@floppysforever:~$ 

```

Thanks again

---

### Post by bodycoach2 on 2008-02-10
Have you tried xmms? On the G3's I've restored with Xubuntu, rhythmbox was also too much a resource hog for those machines. XMMS worked fine.
Also, don't forget the add the medibuntu respository:
[http://www.medibuntu.org/](http://www.medibuntu.org/)
and add the ppc codecs and the ibm java version.

---

### Post by employeeno5 on 2008-02-11
Hi!
Yes, I actually did end up installing xxms. It's running very well. However, to my shock, I'm finding that Amarok is running great. On my Ubuntu install it's a huge memory hog, yet on this slow little machine it's running just great. I'm putting both on with a list of some plusses and minuses of them both.

Thanks for the help!

---


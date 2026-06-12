---
title: "[SOLVED] amarok won't play music"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-08-27
1) I had/have no idea how to "build a collection" or when I do... everythign is blank???
2) When I put songs into a playlist it jsut scrolls from one song to another really fast, not playing a sound

So is this an audio codec problem or my complete incompitence on using this program???

---

### Post by Bachstelze on 2006-08-27
Most likely, it is. Do you ue GStreamer or xine with it ? In a terminal, run

```
dpkg -l | grep amarok
```

and see whether amarok-gstreamer or amarok-xine appears. If it's GStreamer, install **gstreamer0.10-fluendo-mp3** and if it's xine, install **libxine-extracodecs**.

All this asuming you want to play mp3 of course...

---

### Post by altonbr on 2006-08-27
It returned this:

```
ii  amarok                                 1.3.9-0ubuntu4    versatile and easy to use audio player for K
ii  amarok-arts                            1.3.9-0ubuntu4    aRts engine for the amaroK audio player
ii  amarok-engines                         1.3.9-0ubuntu4    output engines for the amaroK audio player
ii  amarok-xine                            1.3.9-0ubuntu4    xine engine for the amaroK audio player

```

I installed 'libxine-extracodecs' but it's still not working... I ran through the first-time setup wizard and told it that my collection is in '/media/brett/music'... and then everything is blank.. so I click 'Playlist > Add Media' and add '/media/brett/music' again.. and that's when the songs scroll and do not work.

---

### Post by Bachstelze on 2006-08-27
Go to Setting > configure Amarok > Engine and make ure you're using xine.

---

### Post by altonbr on 2006-08-27
I am using xine.

See screenshot.

(Look at my collection too; it's blank. It doesn't want to seem to read all the folder in my music folder... I assume it can at least do that... I was using iTunes in windows by the way.)

---

### Post by diepruis on 2006-08-27
You could try upgrading amaroK, that worked for me. See this page: [http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

You could also try setting the "output plugin" to alsa, oss and any other plugins in turn and see if any of them resolve the problem.

Could you also post the output of?
```

dpkg -l | grep libxine-extracodecs

```

Post here if you have any more questions.

BTW: What sound card are you using?

---

### Post by altonbr on 2006-08-27
My sound card is a Audigy 2 ZS so I don't think that's the problem.

The output of 'dpkg -l | grep libxine-extracodecs':
```
ii  libxine-extracodecs                    1.1.1+ubuntu1-2    the xine video/media player library, binary

```

I really think it's something simple that I somehow cannot comprehend... it's the whole 'collection' aspect.

---

### Post by diepruis on 2006-08-27
Well... amaroK skips files it cannot play when building the collection. I know this from personal experience (read frustration). Have you tried the reccomendations in my previous post?

---

### Post by altonbr on 2006-08-27
I'm tried everything that everyone has given me.

[B]
_HymnToLife:_ If it's GStreamer, install gstreamer0.10-fluendo-mp3 and if it's xine, install libxine-extracodecs.

_HymnToLife:_ Go to Setting > configure Amarok > Engine and make ure you're using xine.

_diepruis:_ You could also try setting the "output plugin" to alsa, oss and any other plugins in turn and see if any of them resolve the problem.
[/B]

I just noticed something... it's probably because you referred me to [http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php) and I'm using Ubuntu 6.06 isn't it? God I feel dumb... why is there such a difference between Gnome and KDE?

---

### Post by diepruis on 2006-08-27
> **altonbr said:**
> I just noticed something... it's probably because you referred me to [http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php) and I'm using Ubuntu 6.06 isn't it? God I feel dumb... why is there such a difference between Gnome and KDE?


Nope, that's my fault. Should have noticed you use Ubuntu and not Kubuntu. Sorry.

The differences aren't that great, actually. Gnome and KDE run most apps that are written for each other.

I don't quite follow, however. Did that repo not work for you?

---

### Post by altonbr on 2006-08-27
Well when it says:

```
 wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
deb http://kubuntu.org/packages/amarok-141 dapper main
```

I don't know what to do for the last one

---

### Post by orb9220 on 2006-08-27
Tho I am not sure you also have to install libs for playing mp3's if not sorry but I just install all my codecs so I don't wonder by using  easy ebuntu [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html) or automatix.

[http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)
[http://amarok.kde.org/](http://amarok.kde.org/)

And kde apps run fine in gnome just require kde core libs,

---

### Post by altonbr on 2006-08-27
Yeah I really have no idea what EasyUbuntu did.. just like Automatix... just another piece of software taking up more space on my computer and I have no idea why it removed totem-xine and so on.. I really need to take a course.](*,) 

I'll check out the amarok forum.

---

### Post by ewl1217 on 2006-08-27
What format is the music in? It might just be in a format amaroK can't handle.

---

### Post by diepruis on 2006-08-27
Sorry :)

Try this guide: [http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

### Post by altonbr on 2006-08-27
All of the files are regular MP3 files.. I'm not sure what they're encoded with... some use iTunes, that's all I know.

---

### Post by altonbr on 2006-08-28
Well, I eventually went to /media/brett/ and dragged /music into the collection area... it read the files and eventually played them.. but this means that there 'first-time startup wizard' doesn't work (for me) and that I, and probably many others, won't understand what a 'collection' is.. because I told it where my collection was... and it just sat there and smiled at me (figuratively of course)

---

### Post by orb9220 on 2006-08-28
Is your media/brett/music mounted and read and write accessiable thru fstab?

Is it on a ntfs,fat32,ext3 partition?

---

### Post by altonbr on 2006-08-28
It's a shared fat32 system... I think fstab is what reads it... as far as my knowledge goes... why???

---

### Post by altonbr on 2006-08-28
](*,) 

Ok, so if there is one thing I need, is being able to rip CDs using my music player and letting the music player organize it for me (amaroK does this correct?)

Well no matter if the CD is burned or bought, amaroK can't seem to read the CDs.. let alone rip them... does anyone know what the case may be?

A screenshot is included.

---

### Post by Swistak84 on 2006-10-16
Well i have a problem with amarok and ogg files,
using xine engine,
files are on fat32,
rythmbox plays them okey,

i have all ogg/vorbis libraries i could find, anyone have any idea why amarok won't play ogg ?

---

### Post by DOD1951 on 2006-10-16
Amarok does play ogg files. I have a few of those and it plays them with no problem. I didn't do anything special, that I am aware of, to get Amarok to play them.

---


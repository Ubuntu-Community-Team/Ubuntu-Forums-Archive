---
title: "multimedia on ubuntu"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by boboyii on 2005-12-28
..ok, i'm still a struggling linux ubuntu user, and it seems to work pretty well..I've been floating around this site, and I'd probably have dumped my ubuntu installation in the nearest cyber trash can if not for tips from this forum..

Anyway my installation seems all good and gravy, EXCEPT when I need to access different multimedia types..I know it was rough just looking for an mp3 player, before I found XMMS



One example is this...
Anytime I try to watch a video on Firefox, I get this..

totem cant play f://
Video codec 'MS WMV 9 (win32)' is not handled. You might need to install additional plugins to be able to play some types of movies

I've tried different packages, tried to install plugin's, i've edited the freaking mozpluggerrc file..didnt work.




Also, anytime I try to watch a flash movie, it seems to play sound, but I don't see anything moving. I even reinstalled flash for firefox..still no difference.





I also hate the fact that I have to juggle between different media players..XMMS is fine for mp3's, but when I try to play m4a files, i have to switch to VLC media player..and for wav files, I rely on totem. 




So my questions are
1. Any ideas on how I can streamline my media players, so I can play more than one file type on one player
2. How can I make my firefox play videos???

---

### Post by JimmyJazz on 2005-12-28
mplayer plays all things!

---

### Post by Perfect Storm on 2005-12-28
Fisrt of all which arch of ubuntu are you using? i386 am64? ppc?

If i386:

```

sudo gedit /etc/apt/sources.list

```

add: and also enable universe (remove the "**#**" that's infront of the universe)

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

```

sudo apt-get update
sudo apt-get install w32codecs gstreamer0.8-plugins totem-xine

```

and for DVD movies:

```

sudo apt-get install libdvdcss2

```

You should also try mplayer or vlc and see if its for your likening:

```

sudo apt-get install vlc mplayer-386 mplayerplug-in

```

Instead of mplayer-386 you can choose mplayer-686 if you're using Pentium proccessor.


You may also rread this: [http://doc.gwos.org/index.php/MultiGraphicBreezy](http://doc.gwos.org/index.php/MultiGraphicBreezy)

---

### Post by masingerz on 2006-01-15
Dear Forum:

When I try to open a *.wmv video file I get error: Video codec 'MS WMV 9 (win32)' is not handled. You might need to install additional plugins to be able to play some types of movies

So I tried the suggestion (notice 686):

carlos@masingerz:~$ sudo apt-get install w32codecs gstreamer0.8-plugins totem-xinesudo apt-get install vlc mplayer-686 mplayerplug-in
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs
carlos@masingerz:~$

Please advice on how to proceed.

-masingerz

---

### Post by Perfect Storm on 2006-01-15
Did you add the plf as shown above?

---

### Post by masingerz on 2006-01-15
Dear Articifial Intellingence:

I tried as you suggested to add the plf, and then I tried to apt-get again, here is the output i viewed.



carlos@masingerz:~$ sudo apt-get install vlc mplayer-686 mplayerplug-in
Reading package lists... Done
Building dependency tree... Done
Package mplayer-686 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-686 has no installation candidate

-masingerz

---

### Post by NZ-Wanderer on 2006-01-18
I followed all the steps above and get the same error on the last step...

john@ubuntu:~$ sudo apt-get install vlc mplayer-386 mplayerplug-in
Reading package lists... Done
Building dependency tree... Done
Package mplayer-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-386 has no installation candidate
john@ubuntu:~$

My sources list is as follows: (took out the ## lines so msg wouldn't be too big)

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe
 deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

---

### Post by sabredog on 2006-01-19
Install and run Automatix and all your multimedia woes will disappear, well they did for me :)

cheers

---

### Post by sabredog on 2006-01-19
oops...double post :(

---

### Post by tim15856 on 2006-01-19
[QUOTE=sabredog]Install and run Automatix and all your multimedia woes will disappear, well they did for me :)

cheers[/QUOTE]

I agree. I tried installing all the codecs according to the restricted formats 'how-to'. By the time I was done, nothing worked. Couldn't even play non-encrypted DVDs. Ran Automatix and now all music and video files play.

---


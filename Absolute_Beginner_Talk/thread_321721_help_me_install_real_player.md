---
title: "help me install real player"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by tony2 on 2006-12-19
i tried to install real player. it asked me where to install. i donot know what to do. so i pressed enter and realplayer is installed in the desktop. is there a way to reinstall it? how to install realplayer in usr/local directory. pls give exact syntax. thanx.

Also it doesn't play firefox embedded audio files. pls help as to how to play them too.

---

### Post by sonny on 2006-12-19
You should better use automatix.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

That will install a bunch of sotfware, codecs, apps, etc.

---

### Post by tony2 on 2006-12-19
even that link is server down

---

### Post by sonny on 2006-12-19
try a couple of times... or try this links: [HTML]http://www.getautomatix.com/wiki/index.php?title=Installation[/HTML]

---

### Post by K.Mandla on 2006-12-19
There used to be a RealPlayer 10 deb floating around the wiki somewhere. I had it downloaded and someone else asked me how to install it, and I uploaded it to here:

[http://files.filefront.com/realplayer_1006_00_i386deb/;6339784;;/fileinfo.html](http://files.filefront.com/realplayer_1006_00_i386deb/;6339784;;/fileinfo.html)

(Yeah, I know, it's Filefront. It's the first thing I could find.)

If you download that and double-click on the file, you should be able to install it easy as pie.

It might also be in the commercial repositories, but I've forgotten what's in there these days. :)

---

### Post by tony2 on 2006-12-19
sonny there are two version i386 and 64. which one should i installl. i use pentium 4. pls reply thanks.

---

### Post by tony2 on 2006-12-19
mandla how to uninstall the the real player which i installed in the desktop by mistake. it doesn't play embedded files. is there a way to uninstall it?

---

### Post by bruenig on 2006-12-19
Open a terminal and then copy and paste the following
```
wget http://archive.canonical.com/ubuntu/pool/main/r/realplay/realplay_10.0.8-0ubuntu1_i386.deb && sudo dpkg -i realplay_10.0.8-0ubuntu1_i386.deb
```
That will download the deb, and then install it. It will likely be in /usr/bin, but everything will be tracked by apt, so I wouldn't worry about it. If you ever want to uninstall it, a simple sudo apt-get remove realplay should do the trick.

---

### Post by tony2 on 2006-12-19
mandla i have download the file you mentioned but i want to uninstall the real player which i installed in the desktop directory by mistake and then install it correctly. how to uninstall reallplayer now?

---

### Post by tony2 on 2006-12-19
real player is getting installed thanks mandla and bruenig. but i installed previously realplayer in desktop it is not getting deleted. it says i cannot delete the folder. how to uninstall it? pls help . thankz.

---

### Post by bruenig on 2006-12-19
> **tony2 said:**
> mandla i have download the file you mentioned but i want to uninstall the real player which i installed in the desktop directory by mistake and then install it correctly. how to uninstall reallplayer now?

To uninstall it, delete it. If it is installed on the desktop just delete everything that it put on the desktop, that will uninstall it. Also if you follow my original post, you will not only get real player installed with apt being able to track it but you should be able to play firefox embedded media.

---

### Post by tony2 on 2006-12-19
it says unable to move to trash. access denied.

---

### Post by bruenig on 2006-12-19
> **tony2 said:**
> it says unable to move to trash. access denied.

Get into a terminal, do
```
cd Desktop
```
Then start removing stuff with sudo.
```

sudo rm -rf whatever
```

---

### Post by tony2 on 2006-12-19
that was awesome bruenig. it worked well.

---

### Post by Fully216 on 2006-12-19
You can also install realplay from SPM, assuming you have the correct repos available.  You might also need the automatix repos, which are as follows:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse

try removing the desktop install from a terminal window, so you can use the sudo option.  Better to uninstall via apt though instead of just removing the files, but your choice.

---

### Post by tony2 on 2006-12-19
still real player is not playing embedded files. try this

[http://www.dishant.com/jukebox.php?songid=57141](http://www.dishant.com/jukebox.php?songid=57141)

can you play this ?

---

### Post by tony2 on 2006-12-19
are you able to listen to the song ?

[http://www.dishant.com/jukebox.php?songid=57141](http://www.dishant.com/jukebox.php?songid=57141)

---

### Post by bruenig on 2006-12-19
> **tony2 said:**
> still real player is not playing embedded files. try this

[http://www.dishant.com/jukebox.php?songid=57141](http://www.dishant.com/jukebox.php?songid=57141)

can you play this ?

I don't see anything to play, probably because I am not logged in and am not a member of that site. But here are some things you can do. First go to the address bar in firefox and enter "about: plugins". See what you have in there. Also, I would recommend and I personally use the mplayer plugin to play real media. It plays pretty much everything and so it is nice to have one multimedia plugin that does everything.

Edit: don't put a space between about and plugins like I did above. I had about:plugins but as you can see the : p makes a :p

---

### Post by rowanparker on 2006-12-19
He means ```
about:plugins
``` but a smiley came up instead.

---

### Post by tony2 on 2006-12-19
that site doesnt need a login to hear music. ok wait i will tell u waht i see there in the about:config page. thankz.

---

### Post by tony2 on 2006-12-19
ok i put about:plugins and a lot of things are listed. what do i do now?

i am ok with any player as long as it plays all files including real

---

### Post by tony2 on 2006-12-19
how to make mplayer play these files from this site

[http://www.musicindiaonline.com/music/ut/s/hindustani_instrumental/10/](http://www.musicindiaonline.com/music/ut/s/hindustani_instrumental/10/)

when i try to play the music files. it says "methods are missing". what to do?

are you able to listen any of the song listed in that page ?

---

### Post by bruenig on 2006-12-19
> **tony2 said:**
> how to make mplayer play these files from this site

[http://www.musicindiaonline.com/music/ut/s/hindustani_instrumental/10/](http://www.musicindiaonline.com/music/ut/s/hindustani_instrumental/10/)

when i try to play the music files. it says "methods are missing". what to do?

are you able to listen any of the song listed in that page ?

I can't play anything on that site either. I tried the real media stuff and the windows media stuff and still couldn't get it to work and I know I have the stuff enabled to do so.

---


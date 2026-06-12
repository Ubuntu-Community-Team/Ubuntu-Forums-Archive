---
title: "Online music MP3s etc.."
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by TikkiRo on 2005-12-31
[FONT="Comic Sans MS"][COLOR="Purple"]Probably know the answer to this before I ask it, but want to make sure - is there ANY way of playing online streams which are in RealPlayer or Windows Media player format only?  I listen to talks that only provide these options and can't be downloaded to play 'offline'.  Firefox wanted to just download Win MP for me, but obviously pointless doing that.   

I only installed UB yesterday and still trying to figure out how to get some of my MP3 files to play - proving tiresome at the minute.  Knoppix played them without any problems when I was using it as a boot disk only option, and I sort of figured this OS would do the same :mad: BUT I'm going to stick with it if I can - switching between both this and XP so not overly concerned.  But would like to have access to online media more if I can. [/COLOR][/FONT]

---

### Post by jamesford on 2005-12-31
mplayer + the mplayer firefox plugin might help

---

### Post by TikkiRo on 2005-12-31
You any links for those to download?  I'm lost for finding where half these things are found on the net :)  Thankx for such a fast reply on it tho.

---

### Post by lrmall01 on 2005-12-31
No need to search the net - just use synaptic.  System > Administration > Synaptic Package manager.  Or open a terminal and use apt from the command line.

Try the starter guide for help adding additional software repositories that will have the programs your looking for.  [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Also, Realplayer is available for ubuntu in the multiverse repository.  Go to the website I gave above and search for realplayer - it will show you how to get it installed.

Additionally, MP3s can be played in just about anything (totem, mplayer, xmms, etc.) if you have the right encoders installed.  Again, read the guide that I link to above.

Good luck.

---

### Post by varunus on 2005-12-31
Just open up Help from System->Help, click on the Ubuntu Starter Guide, go to applications, and click "music and movies."  It shows you how to install codecs right there for a bunch of stuff (MP3, MPEG video, etc).

Also, this site:
[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")
shows how to get Real, Windows Media, Quicktime, Divx, and others working.

The reason you can't have these codecs out of the box is due to patent issues; it would be illegal for Ubuntu to include them.  It may be illegal to install some of the codecs as well, depending on what country you're in.  But do what you want...

---

### Post by mztriz on 2005-12-31
```
 sudo gedit /etc/apt/sources.list 
```

Add:

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

```

sudo apt-get update
sudo apt-get install realplay

```
that will install realplayer, and it should work in firefox. :D  (I use it for bbc all the time)

---

### Post by TikkiRo on 2005-12-31
Ok - got working through that lot alright BUT getting this error msg (prob from earlier coding I did for this) :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm the only one using the system so not sure what I've done/not done to provoke this msg?  Any ideas?  Also - although I got MPlayer installed ok - it completely locks up now when I try to play an MP3 with it - can't even close the program using the System processes menu. :(.
TKR

---

### Post by ice60 on 2005-12-31
i've used totem and VLC to listen to real streams, i'm not sure about windows media though.

---

### Post by Jaygo333 on 2005-12-31
Have you tried Automatix.
[http://ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://ubuntuforums.org/showthread.php?t=80295&highlight=automatix)
I installed ubuntu about a week ago and had the same problems as you had but once installed automatix, I got no problems. The program installs the most used 
apps in ubuntu including mplayer, xine(totem) and all codecs used (wmv, mp3).
Try it.

:arrow:h34r: Jaygo333 :arrow:h34r:

---


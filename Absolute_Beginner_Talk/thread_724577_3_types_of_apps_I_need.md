---
title: "3 types of apps I need"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-03-14
Hi,

I recently installed Ubuntu 7.10 32bit on a Dell Inspiron 1521, dual booting Vista.  I am now in need of three types of applications. If they exist, then it would be great to notify me about them. 

The three I need are an MP4/AAC converter, if there is one, a different messenger system other than Pidgin for me to try out (I only need MSN), and an app that can put songs on an iPod, like iTunes.

Thanks
CloudFX

---

### Post by gerod on 2008-03-14
1) MP4/AAC converter: i'm not an expert
2) a different messenger system other than Pidgin: aMSN
3) an app that can put songs on an iPod: I think RythmBox

---

### Post by billgoldberg on 2008-03-14
> **CloudFX said:**
> Hi,

I recently installed Ubuntu 7.10 32bit on a Dell Inspiron 1521, dual booting Vista.  I am now in need of three types of applications. If they exist, then it would be great to notify me about them. 

The three I need are an MP4/AAC converter, if there is one, a different messenger system other than Pidgin for me to try out (I only need MSN), and an app that can put songs on an iPod, like iTunes.

Thanks
CloudFX


1) You could try winff

[http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60](http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60)

2) try amsn, kmess, kopete, ...

3) type ipod in "applications -> add/remove" and pick one.

---

### Post by Oldsoldier2003 on 2008-03-14
> **gerod said:**
> 1) MP4/AAC converter: i'm not an expert
2) a different messenger system other than Pidgin: aMSN
3) an app that can put songs on an iPod: I think RythmBox

kopete is a very nice replacement for pidgin if you want to run a KDE app. it much more full featured than pidgin, aMSN isnt a unified messenger so it really doesn't fit the bill as a pidgin replacement. (yes I know he only needs MSN just making a comment about unified messenger aps, which are much harder to mainatin)

---

### Post by Sef on 2008-03-14
> MP4/AAC converter, if there is one, a different messenger system other than Pidgin for me to try out (I only need MSN), and an app that can put songs on an iPod, like iTunes.

1) Take a look at Sound Juicer CD Extractor.  It can save as MP4/AAC, so it can convert. (Applications > Sound & Video > Sound Juicer CD Extractor)

2) A second on [AMSN]("http://asmn.sourceforge.net").  The only problem I have with it is that once in a while I can't type and have to close it down and reopen it.  To get the newest version (0.97), go to its website; otherwise download the one in the Gutsy repositories (0.96.)  (Applications > Add/Remove > in search, type in AMSN)

3) Also there is Amarok, which is a KDE  app and will install the needed dependencies, if you download it from Add/Remove also.

---

### Post by ramjet_1953 on 2008-03-14
For your iPod, try :

[COLOR="Blue"]gtkpod[/COLOR]

[COLOR="Blue"]Hipo[/COLOR]

For ripping CD's try:

[COLOR="Blue"]Sound Juicer[/COLOR]

[COLOR="Blue"]Ripper X[/COLOR]

Regards,
Roger :cool:

---

### Post by igknighted on 2008-03-15
1) Cannot be done.  MP4/protected AAC is a proprietary apple format with their own DRM.  You cannot convert it, even to use it in other windows applications like Winamp or WMP.  The best you can do is burn them to an audio CD with itunes and re-import them as mp3 or ogg, but be aware that lossy to lossy conversions will further reduce sound quality, so you may want to try it with a few songs to test it.

2) aMSN is popular, but there is a new program (emesen I think) that seems more fully featured.  It is not in the repo's and I don't use MSN messenger, so I can't tell you where to get it.  But a google search should turn it up.  From what I've seen it's an easy install.

3) Any of the major audio players can transfer/remove songs from your ipod.  If you use Gnome, it's a lot like iTunes.  Using Rhythmbox, Songbird, Banshee or Exaile (or probably any other music player) it works in much the same way.  In KDE you can do it through amarok, or even through the file manager (konqueror/d3lphin), as it mounts the ipod via a "kioslave" which will let you drag/drop songs onto it... very convenient.  If you have a new ipod (nano 3g, touch, etc.) you may have to wait for support, because I don't think that those are supported in linux yet.  If there is support, it would likely involve compiling something or running the development (read: unstable, not for use other than bug testing) version of Ubuntu (hardy heron).

---

### Post by CloudFX on 2008-03-15
Thanks for your help, all of you. I now need a mp3 codec to be able to play mp3 files.. how can I get it?

---

### Post by DUDE_2000 on 2008-03-15
media coder (windows only) works a treat for converting all sorts of files. I'ts supposed to work in wine

---

### Post by AndyCooll on 2008-03-15
> **CloudFX said:**
> Thanks for your help, all of you. I now need a mp3 codec to be able to play mp3 files.. how can I get it?
You might be able to do this using Rhythmbox, however I usually use Totem Movie Player.

Open up the app and navigate to an mp3 file. Try playing it ...it should detect that it needs a codec and ask if you want to install it. Obviously you'll say yes!

:cool:

---

### Post by billgoldberg on 2008-03-15
Enter this code for mp3, flash, java, ...

```
sudo apt-get install ubuntu-restricted-extras
```

For dvd support you'll need to add the medibuntu package ([link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")) and give in this command

```
sudo apt-get install libdvdcss2
```

or use vlc media player (sudo apt-get install vlc)

this can't hurt neither

```
sudo apt-get install non-free-codecs
```

---

### Post by CloudFX on 2008-03-15
thanks, I think it worked!

---


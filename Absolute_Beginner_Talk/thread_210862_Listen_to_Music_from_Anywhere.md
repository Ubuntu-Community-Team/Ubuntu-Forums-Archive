---
title: "Listen to Music from Anywhere?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by underdog on 2006-07-07
Hi, I've been running Ubuntu for a while, but I don't know what the best way to do one of the things I want to do with it.:

I want to be able to somehow listen to music on my ubuntu machine from anywhere, whether its with iTunes, WMP, or whatever. I'd like to be able to choose specific songs to stream, preferably. I've done some looking but can't find anything that seems to suit my needs. Thanks

---

### Post by PriceChild on 2006-07-07
I'm not quite sure what you mean :s

If you want to be able to play more types of formats of music:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If you want to use the services such as the itunes store, then a quick search on these forums should provide you with a program that can do this fo ryou.

---

### Post by underdog on 2006-07-07
I see that I wasn't very clear. I want to run a media Server, I want to listen to music that is on my Ubuntu Server from other machines.

---

### Post by PriceChild on 2006-07-07
Ah ok i understand now :)

The way i would do this would to use samba shared folders (samba is availiable in the repos) and link itunes or wmp on the windows machines to the network folders on the ubuntu  machine.

---

### Post by underdog on 2006-07-07
I want to do it over the Internet, though. I know I could play mp3s over a 100mbit ethernet connection without a problem, but I need streaming media server software.

---

### Post by blackpaw on 2006-07-07
I think VLC player is able to encode any type of audio/video content "on the fly" and stream it through your network to whatever device you are using to listen to it.. like a KISS player or whatever. 

As I don't have enough bandwidth to stream video, I usually use **shoutcast** to stream whatever music I play and then just tune in through the built-in webserver :P

if that is what you meant ;)

---

### Post by underdog on 2006-07-07
This looks like what I need, I'll look into it. Thanks for the advice.

---

### Post by echo $USER on 2006-07-07
This is what you are after > sudo apt-get install gnump3dgnump3d is the GNU MP3 media server.  But it can serve any type of media format, streaming or otherwise.  Below is more info on how to configure it to your needs...

[http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server](http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server)

---

### Post by sal_veya on 2006-07-07
Check out Jinzora. It's a fully featured web mp3 player, that allows you to stream all audio files from your webserver. 

[www.jinzora.org](www.jinzora.org)

---

### Post by Maggot on 2006-07-07
> **echo $USER said:**
> This is what you are after gnump3d is the GNU MP3 media server.  But it can serve any type of media format, streaming or otherwise.  Below is more info on how to configure it to your needs...

[http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server](http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server)

I used gnump3d for the past couple years but switched to ampache [http://ampache.org/](http://ampache.org/)

---

### Post by echo $USER on 2006-07-07
> **Maggot said:**
> I used gnump3d for the past couple years but switched to ampache [http://ampache.org/](http://ampache.org/)

Is this free?  Love your shepherds by the way.

---

### Post by underdog on 2006-07-07
It looks like it is...I'm not sure which I'm going to try first. But they all look promising...thanks guys.

edit: Oh man, I'm starting to look at Jinzora....It looks amazing. This is perfect.

---

### Post by djgrandmarquis on 2006-07-09
If you like iTunes, there are several open source implementations of Apple's DAAP protocol. That is, you can set up your Ubuntu box to be an iTunes Shared Music client/server.
[http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol](http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol)

Get It Together is a great DAAP client/server, witten in Java.
[http://getittogether.sourceforge.net/](http://getittogether.sourceforge.net/)

In addition, AmaroK media player has streaming and web browser controls available via scripts. However, they aren't nearly as advanced as Ampache or GNUMP3d.
[http://amarok.kde.org/amarokwiki/index.php/Scripts](http://amarok.kde.org/amarokwiki/index.php/Scripts)

---

### Post by Maggot on 2006-07-10
> **echo $USER said:**
> Is this free?  Love your shepherds by the way.

Yes and thanks, they are awesome dogs ;) 

Did you install Jinzora yet? I looked at it awhile ago but ran into installation problems. No idea what distro I was using at the time. :mrgreen:

---

### Post by mostwanted on 2006-07-10
One of the forum members made something specifically for Ubuntu that can do this:

[http://ubuntuforums.org/forumdisplay.php?f=129](http://ubuntuforums.org/forumdisplay.php?f=129)

---

### Post by underdog on 2006-07-13
Yeah, i messed around with Jinzora some, but unless you get all your music in the initial scan, It won't detect any more for crap. So, I don't suggest it for a usable product right now. I'm sure when it gets better it will, well, be better, but I'm going to look into the other options now :)

---

### Post by andlinux21 on 2006-08-20
When using Jinzora after adding more music and you did a rescan it didnt pick up the new songs?

---

### Post by cjssmo on 2007-08-27
That's actually a bad address go to 

[http://www.ampache.org](http://www.ampache.org)

There is a debian package of ampache in the works.  Check the site it may be up already.

Regards
Charlie  :)

---

### Post by fastpakr on 2007-08-27
> **underdog said:**
> Yeah, i messed around with Jinzora some, but unless you get all your music in the initial scan, It won't detect any more for crap. So, I don't suggest it for a usable product right now. I'm sure when it gets better it will, well, be better, but I'm going to look into the other options now :)

Since this dead thread has already been brought back, I'll get involved...

The above post is not correct (at least not today, perhaps it was when posted.  Jinzora appears to detect new music for me with no problem at all.  I've been using it off and on for a couple of months and it works well.  I can sit at my office pc and listen to any music stored on the home desktop, pull up artist info, lyrics, etc...

---


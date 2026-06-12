---
title: "asx with MPlayer and Firefox"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by bob12564 on 2008-01-21
I'm new to Ubuntu and still trying to configure my system.  I installed the MPlayer plugin and the extra win32 codecs from the MPlayer site as well as the Ubuntu restricted extras.  I am trying to listen to a live radio stream from CBC radio in Canada.  I go to this page:

[http://www.cbc.ca/listen/index.html#](http://www.cbc.ca/listen/index.html#)

I then click the link "Go directly to our full list of streaming URLs" in the blue box.  This opens a popup window with numerous asx links.  I can click on any of them and the MPlayer plugin opens as expected.  I see "connecting" flash quickly and then it says "stopped".  

CBC says this about MPlayer:

For Unix users:

Our CBC radio streams are compatible with Unix
We tested our streams using the Mplayer plugin version 2.66 on:
- Gentoo Linux 1.5.1
- FreeBSD 5.x

Mplayer tends to take longer to connect and buffer the stream
than Windows Media player, so please be patient.

To reduce the buffering time in mplayer, update /etc/mplayerplug-in.conf by uncommenting the following line:

cachesize=256

Xine is another alternative player that works for Linux/UNIX as well



MPlayer supports asx streams and CBC confirms that the Firefox plugin should work.  I tried to edit the mplayerplug-in.conf file as suggested but I don't seem to have the necessary permission to edit the file.  I also tried to right click the MPlayer plugin window which seems to allow changes to the settings but nothing I do makes a difference.  As CBC notes, Xine works well if I copy and paste the link into it.  VLC also works if I copy and paste the link.  I did "about plugins" in Firefox and Player is listed as supporting asx.

I have a work-around solution using Xine and VLC but I like the convenience of just clicking the link and having MPlayer open.  

I appreciate any help.  I've seen other posts on the subject with no real resolution.

Thanks.

---

### Post by nobles on 2008-04-22
Has there been any solution to this yet?  I have had the same problem with mplayer and CBC radio streams on many different distributions.  Alternatively is there something you can install that would do the equivalent of an "open with" that would make this an easier work around?

---

### Post by fromgi on 2008-04-30
I have the same problem.  I can not get asx to play with Mplayer and Firefox on 8.04; however, all other formats do play.

---


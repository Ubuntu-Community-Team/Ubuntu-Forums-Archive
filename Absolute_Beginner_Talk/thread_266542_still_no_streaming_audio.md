---
title: "still no streaming audio"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by slide4417 on 2006-09-27
From previous suggestions, I was able to install RealPlayer10. It now shows up as an application under "sound & video".
But..still when I try to play stuff from the satellite web page...I get a popup that says "Additional plugins required"   (doesn't say what ones though!)   There is another button that says "install missing plugins"  But that doesn't work either...just a window to install manually...I would have expected RealPlayer to pop up when I try to play from streaming audio.
Perhaps RealPlayer needs some setup tickling also???
Thanks all!!

---

### Post by arochester on 2006-09-27
Have you looked at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Scroll down to "Playing Streaming Video from the Internet"

Can you give the exact URL you are trying to get so that others can look and try?

---

### Post by slide4417 on 2006-09-27
I was trying sirius.com....but newsradio88.com does not work either. Probably nothing with streaming audio will work...can't think of anymore at the moment. ](*,) ](*,)

---

### Post by duan on 2006-09-27
many of these streaming sites stream the audio out in mp3 or aac format audio. you'll need to install some codec to interpret this for all the players. I am not shure what codecs come with the plain realplayer installation.

have a look at this help section:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

There is also some dude that wrote a big utility script called automatix to easily install every sort of multimedia plugin for ubuntu.

Not all of it is free and some countries hold a more draconian view on what you can and cannot do with data.

---

### Post by arochester on 2006-09-27
Had a go getting sirius.com and newsradio88.com. I could get them both on Windows and neither on Linux. There seems to be a thing on the Net about sirius.

I've got Automatix.

My Linux vote goes for "Streamtuner"

---

### Post by slide4417 on 2006-09-27
arochester.....can you get any streaming sounds...or sounds off the net on your system???   Ubuntu is kewl, and fun to mess with...but its beginning to be a pretty time-consuming hobby just to get it working.:???:  Reminds me a bit of MAC, but I think MAC sets things up a bit more 'auto' like.

---

### Post by arochester on 2006-09-28
Yes I can get streaming sounds off the Net.

Have you got broadband and  have you installed Automatix - [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by shriphani on 2006-09-28
you need a plugin for the browser itself. i use vlc media player and there's something called mozilla-plugin-vlc for the same. find out about the one for your player.

---

### Post by duan on 2006-09-28
also when you click on a streaming file link you can save the link as a file. The file would normally save as xxx.pls on your desktop (~/Desktop), it is a text file - open it in whatever text editor you like and look at it, there will be a [http://address.of.the.file](http://address.of.the.file) or several if the station has several options.

You can just copy that link and in your default ubuntu Rhythmbox player right click on the radio tab on the left and "add new radio station" and enter that url. Now you don't have to worry about using your web browser and plugins. All you need is the url and the codecs.

Press Ctrl-W in rhytmbox and it minimises to an icon and it just plays in the background.

From now on you'll always have the radio station in rhytmbox and it is faster than going through your browser.

I'm using this right now.

Yes, ubuntu takes a bit getting used to, but the methods don't change from version to version. I messed around with it so much in the beginning thinking I want to use and try everything on the plant, but now I've standardised on the tools I really use and I'm just using it. (same as my wife's mac, it just works).

---

### Post by Das Goat on 2006-09-28
i tried pasteing in the URL to RhythmBox

[http://www.npr.org/templates/dmg/dmg.php?prgCode=ATC&showDate=28-Sep-2006&segNum=&NPRMediaPref=WM&getAd=1](http://www.npr.org/templates/dmg/dmg.php?prgCode=ATC&showDate=28-Sep-2006&segNum=&NPRMediaPref=WM&getAd=1)

RhythmBox didn't know what to do with it. It did try to play the Virgin station that came with Rythm Box, for about half a song. Then it froze up. 

I killed the app, then restarted. now Rhythm Box has nothing in it and will not do squat. Maybe rebooting will help, but i need my NPR on my portch. It is holding me up in my quest to go Windowless.

](*,)

---

### Post by duan on 2006-10-01
I looked inside the link you send (i saved that url to disk and opened it with a text editor).

It looks like some wrapper for a load of microsoft .wma files

One example looks like this.
<ref href="mms://wm.npr.org/wm.npr.na-central/atc/20060928_atc_07.wma

I copied the mms://wm.npr.org/wm.npr.na-central/atc/20060928_atc_07.wma section to rhytmbox and yes, it doesn't know what to do with it.

I had some resluts with gxine. In a terminal I ran 'gxine' (this has always been the tool I had the most succes with playing all sorts of odd media with).

In gxine I 'open mrl' and enter the mms://wm.npr.org/wm.npr.na-central/atc/20060928_atc_07.wma
and it starts buffering and loading it, with a note onscreen that it is windows media audio or some such (ffmpeg). 

It plays about every 100th frame, but this could be my system only. (its a fanless via/cyrix/s3 embedded thing).

I don't remember all the bits I installed but its normally, xine, gxine, gstreamer, and whatever ffmpeg, all the proprietary things.

Honestly I haven't had the time to really figure xine/gxine out but its worth a shot because you can do absolutely anything with (an to) it, so if you have the intention to play every possible sort of media it may be the tool for you.

---

### Post by Das Goat on 2006-10-01
Well, Automatix, now that I understand how to set it up, apparently got the right version of mplayer that lets NPR play through the browser plug ins. I only have two complaints.

1) I really expected that once the stream started, it would load a stand a lone session of the application and not be in the browser window, but that is ok, at least it works, which is more than I can say for any of the other players (XMMS, Listen, Amarok, Streamtuner) that would not work at all or Helix (Realplayer 10) that played it so choppy that it was not listenable. 

2) there are no controls in the browser except pause and stop. NPR listeners know that there are some stories that you don't want to listen to. With no forward button, i have no choice but to listen to them all, or open each story individually.

Anyone have any suggestions (who have actually made this work).

---


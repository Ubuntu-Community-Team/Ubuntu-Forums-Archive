---
title: "How can I view video intended for Windows Media Player"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-12-10
I cannot see a video on a friends website. He tells me that it won't work with Linux because it needs to be viewed using Windows Media Player............... is there an answer around this problem please?

---

### Post by chewearn on 2007-12-10
Whack him in the head for being such a M$ fanboy!
:lolflag:


Seriously though, you could post the link to your friend's website, then we can take a look and give our opinion.

---

### Post by ajgreeny on 2007-12-10
Almost all video file formats can be played and viewed in ubuntu if you install the correct codecs.  So just make sure you have them all and you should be OK.  Have a look at:-
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and also think about enabling the medibuntu repositories after looking at this:-
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and following the advice there.

---

### Post by skymera on 2007-12-10
VLC player, plays almost anything, highly reccomended.

---

### Post by subs on 2007-12-10
try [www.medibuntu.org](www.medibuntu.org)

u will find the codecs for all the windows based media formats....

however the legality of these codecs is under question!!

---

### Post by edm1 on 2007-12-10
```
sudo apt-get install totem-mozilla
```

totem has a windows media player 10 plugin for firefox.

---

### Post by rockinlinux on 2007-12-10
VLC is great, i use it. also i play WMV with the "movie player" that comes stock with ubuntu.....not sure what i installed to get it to work though. A note on VLC and why you should get it: it plays almost everything including DVD's with menus. VLC rocks!

---

### Post by a.v.l on 2007-12-10
> **ajgreeny said:**
> Almost all video file formats can be played and viewed in ubuntu if you install the correct codecs.  So just make sure you have them all and you should be OK.  Have a look at:-
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and also think about enabling the medibuntu repositories after looking at this:-
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and following the advice there.

Thanks for the advice. I'm not sure I've explained myself properly. The website I've mentioned has several videos on different pages. Some videos I can see and some not, there is not even as an empty square box on the page, there is simply nothing there for me to look at. I would appreciate if someone would look at this website and tell me if they are able to view everyl video. The address is 
[www.lost-wax-casting.com](www.lost-wax-casting.com)
I CAN see videos on the jewellery page, but II CANNOT see the video in the Thailand or Bronze Age page. Looking forward to your replies.

---

### Post by stchman on 2007-12-10
> **a.v.l said:**
> I cannot see a video on a friends website. He tells me that it won't work with Linux because it needs to be viewed using Windows Media Player............... is there an answer around this problem please?

Ubuntu can play nearly every type of video file.  Ubuntu can play .wmv files easily.  You will need to install the restriced formats.

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

You should now be able to play the files you want.

---

### Post by ajgreeny on 2007-12-10
There seems to be a problem with the pages on that site [http://www.lost-wax-casting.com/](http://www.lost-wax-casting.com/) that are said to have videos but in actual fact those two don't.  I haven't looked using windows, but it doesn't seem to be a problem of linux but of the pages just missing various elements.

---

### Post by Velcor on 2007-12-10
> **ajgreeny said:**
> There seems to be a problem with the pages on that site [http://www.lost-wax-casting.com/](http://www.lost-wax-casting.com/) that are said to have videos but in actual fact those two don't.  I haven't looked using windows, but it doesn't seem to be a problem of linux but of the pages just missing various elements.

I did, and there isn't anything there. I'm pretty sure I'm not blocking them either.

---

### Post by kefurd06 on 2007-12-10
the video is there in vista w/IE7.
[http://members.cox.net/kefurd06/bronze.png]("http://members.cox.net/kefurd06/bronze.png")

---

### Post by a.v.l on 2007-12-10
> **stchman said:**
> Ubuntu can play nearly every type of video file.  Ubuntu can play .wmv files easily.  You will need to install the restriced formats.

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

You should now be able to play the files you want.

Just an update to say that I have failed to resolve this matter.  To begin with, I thought I had previously installed all of the right codecs using Automatix some twelve months ago, but ran the above in the terminal which more or less told me they were already installed and I had the latest editions. Having done that I still cannot see these videos using Linux Ubuntu so tried using XP.  first with Opera browser which didn't show the video and then with Internet Explorer 6.  With IE6  I had a video window appear on the  Bronze age and the Thailand page but after waiting five minutes the video failed to start.  Thanks for your help, I'll contact my friend and ask him to check things over.

---

### Post by kefurd06 on 2007-12-11
someone should submit this as a bug.... somewhere...

---

### Post by Teknyk on 2007-12-11
This isn't an Ubuntu issue or even a Linux issue.
I just tried using XP with Firefox and it will not show. An XP box that has never even had Linux on it!

This is simply a poorly crafted website.

*Second edit*

validating that page shows a ton of errors
[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.lost-wax-casting.com%2FTHE%2520BRONZE%2520AGE.htm&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.lost-wax-casting.com%2FTHE%2520BRONZE%2520AGE.htm&charset=%28detect+automatically%29&doctype=Inline&group=0)

---

### Post by kefurd06 on 2007-12-11
> **Teknyk said:**
> This isn't an Ubuntu issue or even a Linux issue.
I just tried using XP with Firefox and it will not show. An XP box that has never even had Linux on it!

This is simply a poorly crafted website.

*Second edit*

validating that page shows a ton of errors
[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.lost-wax-casting.com%2FTHE%2520BRONZE%2520AGE.htm&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.lost-wax-casting.com%2FTHE%2520BRONZE%2520AGE.htm&charset=%28detect+automatically%29&doctype=Inline&group=0)

thanks for the clarification teknyk

---

### Post by chewearn on 2007-12-11
Ok, I took a brief look at the website.  The problem is not that the video can only be viewed by Windows Media Player (WMP).  The real problem is the page coding is specific Internet Explorer and WMP syntax.  Which of course, all other W3C standard compliance browsers will not be able to render properly.

Here is an example of the convoluted syntax used to embed the video:
```
<object classid="clsid:6BF52A52-394A-11D3-B153-00C04F79FAA6" id="WindowsMediaPlayer1" width="513" height="443" align="middle" hspace="0"><param name="URL" value="video\Ban Chaing.wmv"><param name="rate" value="1"><param name="balance" value="0"><param name="currentPosition" value="0"><param name="defaultFrame" value><param name="playCount" value="1"><param name="autoStart" value="0"><param name="currentMarker" value="0"><param name="invokeURLs" value="0"><param name="baseURL" value><param name="volume" value="100"><param name="mute" value="0"><param name="uiMode" value="mini"><param name="stretchToFit" value="-1"><param name="windowlessVideo" value="0"><param name="enabled" value="-1"><param name="enableContextMenu" value="-1"><param name="fullScreen" value="0"><param name="SAMIStyle" value><param name="SAMILang" value><param name="SAMIFilename" value><param name="captioningID" value><param name="enableErrorDialogs" value="0"></object>
```The video format is actually wmv, and would have played OK in most browser, if a direct link was provided (or standard compliance syntax is used).  E.g. direct link
[http://www.lost-wax-casting.com/video%5CBan%20Chaing.wmv]("http://www.lost-wax-casting.com/video%5CBan%20Chaing.wmv")

---


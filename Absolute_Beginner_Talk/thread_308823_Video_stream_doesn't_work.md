---
title: "Video stream doesn't work"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by bguy on 2006-11-28
Hi,
I installed all of the video players and codecs using automatix2 and have had success playing video streams from cnn.com, reuters.com and youtube.com but for some reason the stream on the link below doesn't view.  Does anyone know why this is?
I would appreciate any help,
Thanks,
B
[http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///](http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///)

---

### Post by bguy on 2006-11-28
Can any of you view this?

---

### Post by Bloch on 2006-11-28
Yeah, I can view it. 
There are plenty of sites where I can't view the streaming video, but it worked on this one. 

I'm using dapper, and Firefox with the plugins installed by automatix

You can right-click on the mplayer pluigin when it begins to play (or attempts to play) and choose "configure". I am uisng the "gl" output, - I don't know if changing it will help on yours but it's worth a try

---

### Post by bguy on 2006-11-28
Hi Bloch,
I can't see any of the mplayer controls when i open the page.  I've hosted a screenshot to show you exactly what i mean.
[http://img82.imageshack.us/my.php?image=screenshotreportonbusincr5.png](http://img82.imageshack.us/my.php?image=screenshotreportonbusincr5.png)
Thanks a lot for your reply!
B

---

### Post by bguy on 2006-11-28
[http://www.bloomberg.com/avp/avp.htm?T=LiveBTV](http://www.bloomberg.com/avp/avp.htm?T=LiveBTV)

Funny, this feed from bloomberg works for me with ubuntu and under windows it used the same wmp plugin that the robtv one used here.  [http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///](http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///)


Strange! :-k

---

### Post by Robert.Zapata on 2007-01-06
> **bguy said:**
> Hi,
I installed all of the video players and codecs using automatix2 and have had success playing video streams from cnn.com, reuters.com and youtube.com but for some reason the stream on the link below doesn't view.  Does anyone know why this is?
I would appreciate any help,
Thanks,
B
[http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///](http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///)

Hello Team:

I'm also having the same issue. I do not have CableTV service and I depend a lot on watching TV news on the Web. I'm able to see video from CNN, Reuters and MSNBC but I'm a big fan of BloombergTV and the video streams from Bloomberg site do not work. I also llike to watch  the videos from the CBS Innertube site but also they do not work. :( 

[http://www.cbs.com/innertube/player.php?cat=115191&vid=&format=&auto=0](http://www.cbs.com/innertube/player.php?cat=115191&vid=&format=&auto=0)

*(by the way I installed all the codecs including flash 9 with Automatix2 and all my software is up to date in both Dapper and Edgy)*

I installed IE4Linux but when trying to play the Bloomberg video stream it says that BloombergTV requires Windows Media Player v10. :-k 

This issue is in both; Dapper and Edgy

Anyone knows why some sites works and others don't...???

Thanks.

---

### Post by Robert.Zapata on 2007-01-06
> **bguy said:**
> [http://www.bloomberg.com/avp/avp.htm?T=LiveBTV](http://www.bloomberg.com/avp/avp.htm?T=LiveBTV)

Funny, this feed from bloomberg works for me with ubuntu and under windows it used the same wmp plugin that the robtv one used here.  [http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///](http://www.robtv.com/servlet/HTMLTemplate/!robVideo/robtv0726.20061128.00045000-00045280-clip1/h/220asf///)


Strange! :-k

I add the **gl** option but still does not work. ](*,) 

bguy: please, can you elaborate more about the **wmp plugin**...??

Thanks.

---

### Post by petermck on 2007-01-06
I fould this in the page source code.```
<object id="videoie"
  classid="CLSID:22d6f312-b0f6-11d0-94ab-0080c74c7e95"
  codebase="http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab#Version=6,4,07,1112"
  standby="Loading Microsoft Windows Media Player components..."
  type="application/x-oleobject"
  width="304"
  height="291">
```
I'm no expert, but that looks to me as if it's expecting Windows Media Player specific files.

---

### Post by rosswmcgee on 2007-04-06
I get this msg when trying to read Bloomberg.

Totem could not play 'http://ads.blp.valueclick.net/cycle?host=hs0002498=html=indexpage=1;hcat=TVO9;kspd=200;msizes=2x200;bso=listed'.

 There is no media player plug in  to play this.

There is no plugin to handle this movie.

---


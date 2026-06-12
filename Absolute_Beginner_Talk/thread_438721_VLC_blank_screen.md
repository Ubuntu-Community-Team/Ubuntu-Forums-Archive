---
title: "VLC blank screen"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jpboyes on 2007-05-10
Whenever i start a movie in VLC or Movie Player, the screen is black. It will show something if I resize the screen between full screen and normal over and over. Then, if i move anything on the screen , the movie goes black again. Also, is there any way to view streaming real media or window media player?

---

### Post by fakie_flip on 2007-05-10
Install the nvidia driver if you have a nvidia video card.

---

### Post by mbradlcu on 2007-05-10
I had this issue but I believe it was a due to beryl, I think I installed totem-xine and all was good. are your running compiz or beryl?

---

### Post by kaede on 2007-05-10
i do have this similar issue when running beryl, but apparently just if you try to move ur player windows. at first when u play the video. it actually works. but then when u try to move the windows. the image is gone, but the sound still there tough. :D t

---

### Post by Dcox on 2007-05-10
Same issue here with Beryl + VLC. I deactivate beryl to see the vid's actually.
Have an ATI 9800 card.... too bad :(

---

### Post by Michaelt74 on 2007-05-10
Multimedia codecs

Something which caused anguish in the past has been made simple.

Click on Applications>Add/Remove Applications>search for Ubuntu Restricted extras, install these. You will now have most the of the codecs needed to play streaming video and audio. In the same application, search for and install the Flash plugin. Search for and install the VLC Media Player, I found this the most useful and reliable media player to use, especially for streaming.

Firefox media streaming

Search for and install the media player connectivity add on in Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

When it’s installed use the wizard and configure VLC to play all streaming video.

*Note I encountered a problem which resulted in degraded quality when I stream video from Yahoo using VLC, fortunately I found a fix; this may or may not work for you. When you open a link to streaming content from Yahoo, click on ‘Video Quality’, the option next to ‘help’ (your current preference / detected streaming rate is displayed). Mine is 300k. Click on 100k, then ’select’, an advert may reappear, when it’s finished, click on ‘Video Quality’ again and select your original settin (mine was 300k so I clicked it again), then ’select’. When you click on the small ‘play button’ the quality should be greatly improved.

---

### Post by div- on 2007-05-12
Do you have desktop effects enabled and an ATI card? If so, your problem might be due to ATI not properly supporting the composite extension. Turning of desktop effects should fix your problem.

---

### Post by jackhynes on 2007-05-13
It's definately a beryl issue. If you turn beryl off the videos work fine. VLC seems most affected by this bug.

---

### Post by nanceconfer on 2007-05-14
Firefox media streaming

Search for and install the media player connectivity add on in Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

When it&#8217;s installed use the wizard and configure VLC to play all streaming video.
***
I was able to do this installation -- big achievement for the newbie! :) -- but I don't know where to find the wizard. Sorry for the dumb question but if you could point me in the right direction, I'd appreciate it. 

Nance

***
Ooh -- never mind -- I found the wizard -- thanks!! :)

Nance

---

### Post by nanceconfer on 2007-05-14
OK -- VLC wizard located but now I have no idea what to do.

What should I do to set this up to play streaming video from sites with RealPlayer -- like c-span.org?

Thanks.

Nance

---

### Post by aeiah on 2007-05-14
select a different video output option. i think the one you need if you're running beryl is one of the opengl ones.

---

### Post by white3454 on 2007-05-14
I am having the same issue...  Beryl hoses VLC playback.  I have an intel video card on my laptop, I see the output settings in mplayer (opengl) works for .avi files but not DVD playback.  In VLC while running beryl I changed the Deinterlace option to 'X' and it kinda works, I am getting black horizontal bars on the screen and after resize the window goes black.

Video files play well via mplayer with beryl running but DVD playback only works when beryl is not running.  Thanks in advance for any thoughts...

---

### Post by nanceconfer on 2007-05-15
Ummm. . . none of that means anything to me.

Sorry.

I open the Wizard and the first thing I see is Stream to Network or Transcode/Save to File.

I guess and pick Stream to Network.

OK so far?

Then I see a screen that says Select a Stream with a Choose option.

I click Choose and get a screen with tabs -- File, Disc, Network, Video4Linux, PVR, DVB.

Now what?

Thanks.

Nance

---

### Post by kaede on 2007-05-21
try to playing video using totem while running beryl :D

---

### Post by simosx on 2007-06-16
VLC works just fine if you configure it properly. It's just a bit picky the way to configure.
See
[http://simos.info/blog/archives/594](http://simos.info/blog/archives/594)

---

### Post by sailor2001 on 2007-06-16
You have firefox..........in add-ons, search for grease monkey and list the url  in manager user scripts   also you could go to automaix and install restricted codecs

---


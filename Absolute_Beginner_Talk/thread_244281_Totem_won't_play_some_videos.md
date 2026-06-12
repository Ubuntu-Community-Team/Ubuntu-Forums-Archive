---
title: "Totem won't play some videos"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by shyQ on 2006-08-26
After a somewhat successful multi-media install with EasyUbuntu (everything except totem-xine and the repositories change, I am attempting to play videos in web pages.  So far I have 1 success and two failures:

Success - You Tube ([www.youtube.com](www.youtube.com)) videos play successfully

Failures - CNN and Democracy Now

CNN details:
> 
URL: javascript:cnnVideo('play','/video/world/2006/08/25/koinange.obama.return.cnn','2006/09/01');

Message:
Plugin Warning
The CNN viewing experience is optimized for Windows Media Player 9 or above.
No Windows Media Player detected.


Democracy Now details:
> 
URL: [http://play.rbn.com/?url=demnow/demnow/demand/2006/aug/video/dnB20060824a.rm&proto=rtsp](http://play.rbn.com/?url=demnow/demnow/demand/2006/aug/video/dnB20060824a.rm&proto=rtsp)

Message:

Totem could not play 'rtsp://rxns-rbn-sea18.rbn.com/farm/*/demnow/demnow/demand/2006/aug/video/dnB20060824a.rm'. 

Internal GStreamer error: negotiation problem.  Please file a bug at [http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer](http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer) .


I'm out of clues - any help would be appreciated.

Thanks,
J.

---

### Post by Paul133 on 2006-08-26
I don't know. Where'd you get EasyUbuntu?

---

### Post by Crosbie on 2006-08-26
.rm is RealPlayer, I believe... you may need to download that separately.  

I hate RealPlayer. :)

---

### Post by Kobalt on 2006-08-26
Hi,

You actually need more multimedia codecs to play these videos : 
> The CNN viewing experience is optimized for Windows Media Player 9 or above.
No Windows Media Player detected.
The second video is RealPlayer format but you don't need to install RealPlayer to play them, the codecs will suffice. As I don't use (and don't like) Automatix I'll give you a link where you can find a way to install all this easily and in a "regular" way. [Here you go.]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs")
I also recommend you to use MPlayer with its Firefox plugin to play your videos from the web, I personnaly find much more reliable than Totem. If you want to install it, [here is how]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox"). 

Cheerios !

---

### Post by shyQ on 2006-08-26
Thanks Kobalt!

On the assumption that EasyUbuntu installed the codecs correctly, I just did the MPlayer installation.  Without even rebooting, I was able to view both the CNN and Democracy Now videos.  Now on to connecting my Zip drive...

Thanks a bunch.
J.

---

### Post by Kobalt on 2006-08-27
You're welcome ! ;)

---


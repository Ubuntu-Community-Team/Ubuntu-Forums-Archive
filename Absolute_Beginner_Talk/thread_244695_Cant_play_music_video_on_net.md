---
title: "Cant play music video on net"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by BlueLava on 2006-08-26
I just tried to play a music video on tiscali website and get message:
Totem could not play 'mms://mms.cdn-tiscali.com/f2/uk_content/broadband/paul_weller/I wanna Make it Alright _high.wmv'.
followed by: no URI handler implemented for "mms"
Is there a way to play these videos in totem or realplayer 10?

---

### Post by TFX360 on 2006-08-26
```
sudo aptitude install w32codecs
```

if i'm not mistaking.

Kind regards,


TFX

---

### Post by HereInOz on 2006-08-26
Without being able to access the particular area that you are able to, it is a bit hard to test the situation.  Are you able to play other .wmv files in totem?  

Check out:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This may give you a solution to your problem.

---

### Post by BlueLava on 2006-08-26
I got the w32codecs, then tried to watch/listern to bbc weather forcast.
For totem I get message: Totem could not play 'mms://rmv8.bbc.net.uk/news/olmedia/n5ctrl/summaries/weather/hc_weather_uk_bb.wmv'.
followed by: no URI handler implemented for "mms"
& for realplayer I get message:The player does not have the capabilities to play back this content, The following components are required:mms
URL:mms://rmv8.bbc.net.uk/news/olmedia/n5ctrl/summaries/weather/hc_weather_uk_bb.wmv
I hope this helps you to help me.

---

### Post by TFX360 on 2006-08-27
> **BlueLava said:**
> I got the w32codecs, then tried to watch/listern to bbc weather forcast.
For totem I get message: Totem could not play 'mms://rmv8.bbc.net.uk/news/olmedia/n5ctrl/summaries/weather/hc_weather_uk_bb.wmv'.
followed by: no URI handler implemented for "mms"
& for realplayer I get message:The player does not have the capabilities to play back this content, The following components are required:mms
URL:mms://rmv8.bbc.net.uk/news/olmedia/n5ctrl/summaries/weather/hc_weather_uk_bb.wmv
I hope this helps you to help me.

Change or add this line to your 

```
sudo nano /etc/apt/sources.list
```

```
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
```

```
Crtl+X
```
```
Enter
```
```
Enter
```

Then do the following:

```
sudo aptitude install totem-xine gxine libxine-extracodecs mplayer
```


This works for me so let me know if it does for you.


The multiverse solves an update problem, if you don't change that update manager and aptitude will nag.


Kind regards,


TFX

---

### Post by TFX360 on 2006-08-27
This really makes Ubuntu less for human beings. Codecs an GNU/GPL.

I just watched the weather with a nice colored man in a nice suit. Works like a charm here.


Kind regards,


TFX

---

### Post by BlueLava on 2006-08-27
Followed your instructions TFX360 & it works great. I can now see the weather & watch all the music videos/trailors on tiscali that I couldnt access before.
A Very BIG Thankyou!

---

### Post by TFX360 on 2006-08-27
Your quite welcome! Have fun with it!


Kind regards,


TFX

---


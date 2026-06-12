---
title: "Net ATI drivers almoust working"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by BurKaBU on 2008-02-28
I've had some problems installing the new ati drivers on my HP nx9420 with a x1600 card.
Since I'm very new at Ubuntu (2 days :) ), I've just lurked around these great forums and tried every guide and command there is, usually just blindly copy-paste in stuff in my console, and eventually got it working so that I can enable the visual effects.
The problem is when I try watch something on my vlc player the image keeps flickering around and I have to say no matter how great I can make my desktop look I still prefere watching a movie on my vlc :P

So if anyone have any ideas I would greatly apreciate it.

---

### Post by S15_88 on 2008-02-28
pretty sure with ati x1... cards all you need to do is enable the restricted driver: System>Administration>restricted drivers

but if you have it working then it's upto you as for VLC try disabling the visual effects while you watch the movie, does that work?

Thanks, ALain

---

### Post by BurKaBU on 2008-02-28
> **S15_88 said:**
> pretty sure with ati x1... cards all you need to do is enable the restricted driver: System>Administration>restricted drivers

but if you have it working then it's upto you as for VLC try disabling the visual effects while you watch the movie, does that work?

Thanks, ALain

Yes i have the restricted drivers enabled and it says its in use but the box isnt filled in (but read that it was normal).
And sure I can keep switching the effects on and of, but that feels more like a Windows solution :P

---

### Post by S15_88 on 2008-02-28
is it fullscreen only or any screen size, have you tried more than one DVD?

Thanks, ALain

---

### Post by BurKaBU on 2008-02-28
> **S15_88 said:**
> is it fullscreen only or any screen size, have you tried more than one DVD?

Thanks, ALain

Well its actually not in fullscreen, only in non-fullscreen.
And I havent tried DVD, 99.9% of the time I'm watching downloaded series.

---

### Post by S15_88 on 2008-02-28
perhaps it's a problem with your downloaded files?  the only reason i can think that desktop effects would be causing this is you say the problem stops when they are disabled.

---

### Post by BurKaBU on 2008-02-28
> **S15_88 said:**
> perhaps it's a problem with your downloaded files?  the only reason i can think that desktop effects would be causing this is you say the problem stops when they are disabled.

Now Ive tried ~50 different .avi .mpg .asf files and they are all behaving this way when I enable the background. And apart from that the quality etc. is very good.
So I doubt its the files that are the cause of the problem?

And now it wont stop flickering even in fullscreen, wihout me even touching something...

---

### Post by gloscherrybomb on 2008-02-29
same problem on my x1650 pro card. I have tried both restricted drivers and envy drivers. using metacity improves it but is still to bad to watch. This is with a multitude of videos, and different programmes. I also have problems with screensavers.

---

### Post by BurKaBU on 2008-02-29
> **gloscherrybomb said:**
> same problem on my x1650 pro card. I have tried both restricted drivers and envy drivers. using metacity improves it but is still to bad to watch. This is with a multitude of videos, and different programmes. I also have problems with screensavers.

Didnt notice the screensaver until you pointed it out, and I  may also add that it doesn't matter if I use mplayer, vlc or the movieplayer... it still flickers whenever I have screen effects turned on :(

---

### Post by miciurin on 2008-03-01
I had the same problem with flickering videos. If you have compiz enabled (the 3D desktop) then go in VLC, settings, preferences. First check the Advanced options, then in video, output modules, change it from default to X11. Save and restart VLC. Your videos will stop flickering now regardless of the eye-candy.  Same in the other players that you want to use with compiz enabled.  

I must say that this seems to be related to ATi drivers only.

---

### Post by gloscherrybomb on 2008-03-02
> **miciurin said:**
> I had the same problem with flickering videos. If you have compiz enabled (the 3D desktop) then go in VLC, settings, preferences. First check the Advanced options, then in video, output modules, change it from default to X11. Save and restart VLC. Your videos will stop flickering now regardless of the eye-candy.  Same in the other players that you want to use with compiz enabled.  

I must say that this seems to be related to ATi drivers only.

This improves the situation as I stated above but the quality is still poor. Looking on other forums it seems it may be to do with the ati drivers. The video tears and can sometimes look a bit pixelated.

---


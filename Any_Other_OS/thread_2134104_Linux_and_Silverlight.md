---
title: "Linux and Silverlight?"
date: 2013-04-10
forum: Any Other OS
---

### Post by Gael33 on 2013-04-10
I live in a conservation property that will not allow Sat Dishes. Terrestrial TV is all we have ... No cable like Virgin Media.
My OS is Linux Mint 14 Cinnamon 64 bit and I was advised to download Novell-Moonlight as a linux replacement for Silverlight which is necessary to run "Now TV". I tried Google Chrome Browser and Chromium with Novell Moonlight, neither of them work and I still get asked to install Silverlight. I have read that Silverlight does not support Linux and seen lots of frustrated complaints about the inability to get Silverlight / Moonlight working in Linux. The question is, has anyone ever got Moonlight to work? Perhaps I'm using the wrong Browser and that may be my problem or is there another way that will work?

Any help on this would be really appreciated.

Thanks.

---

### Post by howefield on 2013-04-10
Thread moved to the "Other OS/Distro Support" forum.

---

### Post by Gael33 on 2013-04-10
Thank you :)

---

### Post by howefield on 2013-04-10
You're welcome.  :-)

I don't rate your chances of getting a positive outcome for your query, although I don't use Mint I do use (at least, for a few more weeks) sky tv services and Sky Go can't be persuaded to work, I'd expect that NowTV would be similar.

Sadly, your best chance is probably going to be a virtual machine.

---

### Post by Gael33 on 2013-04-10
Yes, I was considering a VM but thought I should investigate other avenues first ... I'll make a start with Virtual Box and see where I go from there :)

Thanks again.

---

### Post by 3rdalbum on 2013-04-12
I believe Silverlight has been abandoned by Microsoft as almost nobody developed anything with it. Moonlight development stopped in 2011 too. I never got anything to work in Moonlight, in my extremely limited testing.

Sorry it doesn't help you. There might be alternatives for TV-watching that you could try?

---

### Post by kurt18947 on 2013-04-12
I suspect you'd need to do something like has been done with Netflix.  Unfortunately, the solution linked to below requires a custom version of WINE plus a dedicated app.

[http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019)

---

### Post by howefield on 2013-04-12
> **3rdalbum said:**
> I believe Silverlight has been abandoned by Microsoft as almost nobody developed anything with it. Moonlight development stopped in 2011 too.

Hmm, last release of Moonlight appears to have been only a few weeks ago.

No matter in this case, it aint gonna work ;-)

---

### Post by Gael33 on 2013-04-12
> **3rdalbum said:**
> I believe Silverlight has been abandoned by Microsoft as almost nobody developed anything with it. Moonlight development stopped in 2011 too. I never got anything to work in Moonlight, in my extremely limited testing.

Sorry it doesn't help you. There might be alternatives for TV-watching that you could try?

Yep! I tried Moonlight and it was rejected by Now TV ... It has to be the most up-to-date Silverlight to function.

---

### Post by jawilljr on 2013-04-12
One thing to try is to install [netflix-desktop](http://www.compholio.com/netflix-desktop/) and run firefox.exe with the following command:

```
export WINEPREFIX="/home/jawilljr/.wine-browser";/opt/wine-compholio/bin/wine ~/.wine-browser/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```

Change "/home/jawilljr" with your user name.

The above command works with [this test video.](http://www.iis.net/media/experiencesmoothstreaming)

Hope it works.

Jerry

---

### Post by Gael33 on 2013-04-12
> **kurt18947 said:**
> I suspect you'd need to do something like has been done with Netflix.  Unfortunately, the solution linked to below requires a custom version of WINE plus a dedicated app.

[http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019)

Interesting article ... I did consider trying through Wine but I'd already moved on and installed VirtualBox, installed my wife's old Windows XP Professional and customised it. Now TV downloaded "Silverlight" and as far as I can see, it should work ... I'll try it at the Weekend and let you know :)

---

### Post by Gael33 on 2013-04-12
> **jawilljr said:**
> One thing to try is to install [netflix-desktop](http://www.compholio.com/netflix-desktop/) and run firefox.exe with the following command:

```
export WINEPREFIX="/home/jawilljr/.wine-browser";/opt/wine-compholio/bin/wine ~/.wine-browser/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```

Change "/home/jawilljr" with your user name.

The above command works with [this test video.](http://www.iis.net/media/experiencesmoothstreaming)

Hope it works.

Jerry

I guess Netflix and Now TV work differently ... hey-ho! :)

---

### Post by jawilljr on 2013-04-12
> **Gael33 said:**
> I guess Netflix and Now TV work differently ... hey-ho! :)

Sorry...thought it was worth a shot.

Jerry

---

### Post by Gael33 on 2013-04-12
> **jawilljr said:**
> Sorry...thought it was worth a shot.

Jerry


Thanks Jerry, it is always worth a shot. You never know when someone will hit the target and that will be another problem solved :)

I appreciate all your efforts 

gael

---

### Post by anbj on 2013-06-29
I think you should try [http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019). I have tested other streaming sites also. Just hit F11 to get out of full screen mode and F10 to show menu. I have managed to download and update Silverlight to the latest version and also download and install Adobe version 11.1.10. It works flawlessly on my system Ubuntu 32-bit 12.04 LTS.

---

### Post by BubuXP on 2013-06-29
In Italy, the national TV uses only Silverlight for streaming.
Someone found a workaround to play the streams installing only a firefox addon
[https://addons.mozilla.org/it/firefox/addon/raismth/](https://addons.mozilla.org/it/firefox/addon/raismth/)
and I remember that this has been used to play other streams as well, maybe without "hacking" the code inside the addon.
My two cents...

---

### Post by Erik1984 on 2013-06-29
> **3rdalbum said:**
> I believe Silverlight has been abandoned by Microsoft as almost nobody developed anything with it. Moonlight development stopped in 2011 too. I never got anything to work in Moonlight, in my extremely limited testing.

Sorry it doesn't help you. There might be alternatives for TV-watching that you could try?

Silverlight seems abandoned but -sadly- still widely used.

---


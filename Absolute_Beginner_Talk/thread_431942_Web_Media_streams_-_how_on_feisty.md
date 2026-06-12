---
title: "Web Media streams - how on feisty?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by blop on 2007-05-03
Hi,

i have just setup kubuntu 7.04 and im struggling to play streaming media from the bbc site, i can now do you tube but not bbc.

i have installed the restricted repositries package.

cheers!

---

### Post by starcraft.man on 2007-05-03
[This]("https://addons.mozilla.org/en-US/firefox/addon/446") is a great addon.

Install it and make sure when you configure it all streams to totem (if your gnome, KDE is kaffeine I think). As long as you have all your codecs, should be fine.

---

### Post by blop on 2007-05-03
hi, thanks for the response...

i have that plugin for firefox but it does not work...

---

### Post by starcraft.man on 2007-05-03
> **blop said:**
> hi, thanks for the response...

i have that plugin for firefox but it does not work...

Eh? Really? Gah, what kind of stream are they using? Click your media player connectivity icon in the lower right, then tell it to list the media. What is the format of the stream? I don't watch bbc so I don't know >.> It should be supported by the codecs.

---

### Post by LuisGMarine on 2007-05-03
May I recommend that you try out [VLC]("http://www.videolan.org/vlc/")?

The install directions are on there, when you click on the Ubuntu Linux link.  

I'm using it right now to play everything from wmv's , divx, mpegs, etc.  Everything is working just fine, I would recommend this to anyone :)

Good Luck

-LuisGMarine :guitar:

---

### Post by blop on 2007-05-03
its real media player...

but i have installed real player 10 with deb package.

ill check out vlc

---

### Post by starcraft.man on 2007-05-03
> **blop said:**
> its real media player...

but i have installed real player 10 with deb package.

ill check out vlc

Ah, thats easy... I don't think totem or vlc play RM, its a silly format...

Long as you have the format installed, all you have to do is change Real Player to stream it.

Click Tools > Media Player Connectivity > Configure.

Find the Real Media line and then in the text box to the right, just paste in the following.
```

/usr/bin/realplay
```

That should do it with minimal effort.

Alternatively, if you want to reconfigure other formats in future, just click the wizard tab in the media player window and click that, when its done scanning and you see the formats real or any other player will be in the drop down :)

---

### Post by blop on 2007-05-03
thats done it!!

cheers!

wonder if it works in opera...

---

### Post by starcraft.man on 2007-05-03
> **blop said:**
> thats done it!!

cheers!

wonder if it works in opera...

Your welcome, if opera makes its own real plugin then I guess it would stream. I don't use opera, I doubt they have a plugin as nice as media player connectivity :).

---

### Post by LuisGMarine on 2007-05-03
> **starcraft.man said:**
> [This]("https://addons.mozilla.org/en-US/firefox/addon/446") is a great addon.

Install it and make sure when you configure it all streams to totem (if your gnome, KDE is kaffeine I think). As long as you have all your codecs, should be fine.

Thanks for that link to that plugin its great.  For some reason VLC was messing around with me today and wasn't working well, I changed to totem ( for some reason videos on totem have better sound then VLC ) , so I came back isntalled that plugin and everything is running very smooth.  Thank you :)

---

### Post by Michaelt74 on 2007-05-03
I use VLC and it's the best option for media streaming I've seen so far. Check out this link to configure Firefox for streaming.

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

Good luck!

---

### Post by starcraft.man on 2007-05-03
> **LuisGMarine said:**
> Thanks for that link to that plugin its great.  For some reason VLC was messing around with me today and wasn't working well, I changed to totem ( for some reason videos on totem have better sound then VLC ) , so I came back isntalled that plugin and everything is running very smooth.  Thank you :)

Your welcome, glad to be of service, I just love it when more than one person gets help from my posts, cuts down on my typing :p

---

### Post by blop on 2007-05-04
cheers i will check that out when i get home..

Is there a similar plugin for opera? as im really an Opera fan at heart...

---


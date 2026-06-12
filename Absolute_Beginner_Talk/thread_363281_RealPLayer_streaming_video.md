---
title: "RealPLayer streaming video"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Bloch on 2007-02-16
Can someone check to see if ther realplayer plugin works for video on the RTE site.
[http://www.rte.ie/news/index.html](http://www.rte.ie/news/index.html)

It worked for me until a few days ago. Now I get only sound and no image. (It plays on my mac so I know the site is working OK)

I would like to let them know if it is a problem on their side - they mention linux on the site so they are aware of linux users. 

I also cannot get the streaming video to work on the BBC site, but t has never worked for me there.

---

### Post by jordanmthomas on 2007-02-16
Works for me -- I use the mplayer plug-in.  Maybe you should switch to it instead of the realplayer plugin?

---

### Post by Red Knuckles on 2007-02-17
> **Bloch said:**
> Can someone check to see if ther realplayer plugin works for video on the RTE site.
[http://www.rte.ie/news/index.html](http://www.rte.ie/news/index.html)

It worked for me until a few days ago. Now I get only sound and no image. (It plays on my mac so I know the site is working OK)

I would like to let them know if it is a problem on their side - they mention linux on the site so they are aware of linux users. 

I also cannot get the streaming video to work on the BBC site, but t has never worked for me there.

I have video but no sound with RealPlayer. I have no sound in RealPlayer anywhere video or audio. Wish I knew why???:confused:

---

### Post by Red Knuckles on 2007-02-18
I got video and sound from [http://www.rte.ie/](http://www.rte.ie/) and [http://www.bbc.com](http://www.bbc.com) now. The mplayer plugin is playing video with sound. For the radio pages I uninstalled RealPlayer and installed gxine, gxine-plugin, kaffeine-plugin. For these 2 websites gxine works for me. For [http://www.npr.org](http://www.npr.org) kaffeine works.
:guitar: :lolflag:

---

### Post by Red Knuckles on 2007-02-18
I've just figured out how to get sound from RealPlayer in Firefox and Swiftfox:

sudo aptitude install alsa-oss
sudo kwrite /usr/lib/realplay-10.0.8/realplay

edit this line [It's line 73]

$REALPLAYBIN "$@"

to read:

aoss $REALPLAYBIN "$@"

reboot and you should have sound in RealPlayer on the mentioned web sites.
:lolflag: :guitar:

---

### Post by divali on 2007-03-07
Using Fiesty.
Well thanks for your last post , that worked for me.

---

### Post by bwallum on 2007-03-08
Just spent the day struggling with BBC news. Cracked it by carefully following this [https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

Hope it helps

---


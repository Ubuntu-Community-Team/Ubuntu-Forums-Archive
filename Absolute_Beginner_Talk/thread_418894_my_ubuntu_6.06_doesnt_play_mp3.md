---
title: "my ubuntu 6.06 doesnt play mp3"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by alket on 2007-04-22
my ubuntu 6.06 doesnt play mp3 ?? how can i add a plugin to play mp3 ?

---

### Post by bobplano on 2007-04-22
read this: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

mp3 codec's aren't included by default because they are not free. automatix is another way to easily get codecs but some people will tell you that it can mess up your system. personally i had no problems with it though

---

### Post by mikewhatever on 2007-04-22
Have you tried this? [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

---

### Post by alket on 2007-04-22
i live in kosovo its not a problem for that we dont have law for computing

---

### Post by zvacet on 2007-04-22
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by bobplano on 2007-04-22
it is not because it is against the law, it is because it is not free or open source, and with dapper and edgy at least they chose only free or open source software so there wasn't a chance for them including stuff you had to pay for

---

### Post by alket on 2007-04-22
ok is there any way to take mp3 or not cause i didnt understood well

---

### Post by Andyfield123 on 2007-04-22
Which player are you trying to use ???
I had this problem, but found many more players that did not need the codec installing.
XMMS is good, Quod Libet and if you try Amorok when you try to play an mp3, it asks if you want to install the codec or something. Follow that and choose to enable the multiverse option or something like that and it should play the next time you try playing an mp3!
Also You can install EasyUbuntu, which will enable the option to install alot of usefull codecs.

---

### Post by mikewhatever on 2007-04-22
> **babaroga said:**
> ok is there any way to take mp3 or not cause i didnt understood well

Have you looked at the links many of us posted? 
> sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

---

### Post by alket on 2007-04-22
thnx a lot

sorry for my english

---

### Post by hugmenot on 2007-04-22
> **bobplano said:**
> it is not because it is against the law, it is because it is not free or open source, and with dapper and edgy at least they chose only free or open source software so there wasn't a chance for them including stuff you had to pay for

That is utter nonsense. All the MP3 decoders in Ubuntu are free and open source. It&#8217;s merely a patents issue.

---


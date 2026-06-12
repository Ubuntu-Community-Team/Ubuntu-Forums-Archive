---
title: "Question about Rhythmbox"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-25
I love Rhythmbox. But the question is can it play .m4a? If it can't, is there any codec?

---

### Post by Darrious on 2006-11-25
I do not use Rythmbox very much so I do not know. 

I would just install mplayer.

---

### Post by Delkster on 2006-11-25
Yes, Rhythmbox can play unprotected m4a files, assuming that the appropriate codecs are installed. It can't play encrypted files from iTunes, though. The package you'll need is probably **gstreamer0.10-plugins-ugly**. You should be able to find the codec package in the following way:

1. Open **Applications > Add/Remove**
2. Make sure to select that all applications be shown rather than only the officially supported ones.
3. Search for **codec**
4. You should now see "**GStreamer Extra Plugins**". Once you select the checkbox next to it, Add/Remove Applications will probably prompt you that it needs to enable the "multiverse" channel. (The codecs aren't included in the default installation and are placed in multiverse instead of the officially supported one due to patent restrictions.)
5. After Add/Remove Applications has finished enabling the channel, click on either "**Ok**" or "Apply" to install the package. If you want, you can also install the GStreamer ffmpeg video plugin and Xine extra plugins if you want. That mostly pertains to video formats and codecs, but it can improve support for some of those in other applications.

If you can't find those packages in Add/Remove Applications, you can try searching in Synaptic Package Manager by the package name I mentioned early in the post. You'll need to enable the multiverse channel by hand for that -- check out the [instructions in the Ubuntu Wiki](https://help.ubuntu.com/community/Repositories/Ubuntu).

---

### Post by oliviacond on 2006-11-25
I have installed gstreamer0.10-plugins-ugly means I can play .m4a, izit?

---

### Post by Delkster on 2006-11-25
> **oliviacond said:**
> I have installed gstreamer0.10-plugins-ugly means I can play .m4a, izit?

Yes, as far as I know. Have you tried?

---

### Post by oliviacond on 2006-11-25
nope. All my songs is in my 2nd hdd. Places>Computer can't detect it. Fixing it now. I will post the result as soon as the "Computer" detect the hdd.

---

### Post by oliviacond on 2006-11-25
But whenever I open a .m4a , the Ryhthmbox go to play other .mp3 . I think is not the codec causes the problem, I think is the Rhythmbox problem

---


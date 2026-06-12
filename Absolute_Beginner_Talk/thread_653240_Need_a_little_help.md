---
title: "Need a little help"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by steve70 on 2007-12-29
What goes on everybody?

I'm really enjoying Ubuntu. This is one of the those "computer projects" that keep a noob like me in his chair staring at the monitor for hours on. I do have one situation. When I access web sites to run a music stream, I can't get it going. I installed the latest Java release, but to no avail. Can some one tell me what I'm missing here?

(If I don't reply right away, I left for Barnes and Noble to get me a book on Ubuntu...honest!):lolflag:

---

### Post by AndyCooll on 2007-12-29
> **steve70 said:**
> What goes on everybody?

I'm really enjoying Ubuntu. This is one of the those "computer projects" that keep a noob like me in his chair staring at the monitor for hours on. I do have one situation. When I access web sites to run a music stream, I can't get it going. I installed the latest Java release, but to no avail. Can some one tell me what I'm missing here?

(If I don't reply right away, I left for Barnes and Noble to get me a book on Ubuntu...honest!):lolflag:

What error message do you get? Can you give us an example of a music stream you are trying to access?

:cool:

---

### Post by Perfect Storm on 2007-12-29
You properly need, mplayer mplayer browser plugin and codecs to hear those. If it's flash based you need flash ofcause;

In the terminal
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo aptitude install w32codecs ubuntu-restricted-extras libdvdcss2 mpg123
sudo aptitude install mplayer mplayer-fonts mozilla-mplayer mencoder
```

Should do it.

---

### Post by steve70 on 2007-12-30
AndyCooll and AI...thanx for the feedback. 

I was on a website (motionfm.com) and I couldn't hear anything,,,No error messages displayed

As for the code, I'm going to try it out today...I also found another method for my test desktop....

Try Rhythmbox, and grab this from Sympatic Package Manager as my codec

*gstreamer-plugin-ugly-multiverse*

('Hope it works...')

---

### Post by steve70 on 2007-12-30
AI

Much love on the code!!!!!! Looks like everythings good. Java installation really helped this to load smoothly!

---


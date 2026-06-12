---
title: "iPod 8gb Nano and Gtkpod Crashing"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by buffybot5 on 2008-01-30
Hi all, 
I definitely need some help with my new ipod nano 8gb.  I managed to download songs on it via gtkpod.  After 50+ hours at the computer, this was a miracle. Of course, I couldn't actually play the songs on my ipod :( So, 50 hours down the drain.

 Now, though, gtkpod crashes if the iPod is connected.  

Running it from terminal, I get this message:  

** (gtkpod:26077): CRITICAL **: ipod_parse_artwork_db: assertion `itdb' failed
Segmentation fault (core dumped)

Rhythmbox won't even detect the ipod. Gpodder actually does connect to it and puts podcasts on it.  Except I can't hear them! I've had little luck with Banshee, Songbird, or Exaile, either.

I am very new to this, so if anyone is willing to explain in super easy terms, how to fix these problems, I will give my first born child.

---

### Post by startherepodcast on 2008-01-31
You said you tried everything, did you try updating GTKPod. Apple altered the way you fill an iPod with the new generation, they built some secret chip into it to annoy everybody.

[http://www.gtkpod.org/downloads.html](http://www.gtkpod.org/downloads.html)

Hope that helped!

---

### Post by buffybot5 on 2008-01-31
Thank you for the link.  Sad to say....but the README file offered by gtkpod is a little too complicated for me.  I'm going to pour over it to see if there is a solution in the guide, though.

---

### Post by buffybot5 on 2008-01-31
Ok, so what I've figured out from your very helpful link, is that I need to compile and install libgpod 0.6.0 or SVN adn then run Amarok or GTKpod against it.  

I'm really new to this.  How do I do that?  I've looked at the extracted files, but its Greek to me.

---

### Post by jdong on 2008-01-31
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Set up and upgrade your gtkpod and friends from the above mentioned repository. I know it says iPod Touch but the upgraded gtkpod packages also apply to new generation classics and nanos.

---

### Post by buffybot5 on 2008-02-01
Thanks for the link!  I followed the instructions (well, some of them, anyway.  IPod Convenience would not load from Synaptic.)  I got rid of GtkPod, as I am too inexperienced to install 0.99.12, and used Amarok, instead.  For right now, I can load podcasts only (and very very very slowly).  Still better than nothing! 

I will hopefully learn how to build gtkpod .99.12 from the source, then maybe I'll be able to add actual music tracks to the ipod.

---


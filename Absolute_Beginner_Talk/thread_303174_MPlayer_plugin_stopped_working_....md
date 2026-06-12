---
title: "MPlayer plugin stopped working ..."
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-11-19
Ok, so my friend was using my firefox and he tried to view a movie, but for some reason MPlayer plugin isn't working. It gets up to 99% and then just freezes. I tried other sites, too, just to make sure it wasn't the one site, but no luck. We tried restarting the computer, too, and again it still doesn't work. Can someone help?

---

### Post by kbsuperstar on 2006-11-19
bump

---

### Post by taurus on 2006-11-19
Maybe remove it and reinstall it again...  You can use automatix2 to install a mplayer plugin for your firefox!

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by kbsuperstar on 2006-11-19
Nope, didn't work.

Now, it just downloads the whole thing and then stops.

Ugh..... What do I do?!

---

### Post by taurus on 2006-11-19
Are you using firefox 1.5 or 2.0?  And if you are using firefox 1.5, I assume you are running Dapper and if you are using firefox 2.0, then you are probably running Edgy unless you upgrade your firefox from 1.5 to 2.0 in Dapper!  What is the url of the site?

---

### Post by kbsuperstar on 2006-11-20
I'm using firefox 1.5 and Dapper. It's not a particular site, it's all movies that MPlayer regulates (I've tried a few different sites that play movies).

---

### Post by Fully216 on 2006-11-20
Have you installed restricted formats (I would assume so because you used automatix)?

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by kbsuperstar on 2006-11-20
As far as I know, yes. It used to work, and it just stopped working all of the sudden yesterday.

---

### Post by kbsuperstar on 2006-11-20
I think it's the fact that I had to reset my xserver, and now my video card is labeled "nv" in /etc/X11/xorg.conf . I forgot how to install nVidia drivers. Anyone have a good tutorial?

---

### Post by kbsuperstar on 2006-11-20
bump

---

### Post by Fully216 on 2006-11-23
The nvidia drivers can be downloaded from their website.  You do not need a tutorial.  They have an application that will do the installation for you once you run the 'sh' file.  It will even configure your xserver too with some default settings, that are very good in most cases.

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

---

### Post by r4ik on 2006-11-23
> **kbsuperstar said:**
> Nope, didn't work.

Now, it just downloads the whole thing and then stops.

Ugh..... What do I do?!

Right click screen and select video output ?

Good luck !

---

### Post by Kubunteando on 2006-11-23
I have found in then mplayer man pages that the -wid option is not valid with the "xv" video driver. This option is used when launching the mplayer from Firefox. So I instead use the "x11" video driver. To change so you can right click the video windows that opens on the browser, go to configure and set the Video Output to "x11". Or better go to the ".mplayer" folder on you home directory and edit the file "mplayerplug-in.conf" and add a line with "vo=x11".

I can open ASX, and WMV. The BBC works in a weird way: or I hear it or I see it, but not both at the same time. So I copy the link and I paste it in Real Player 10.

I am using edgy and it works fine. I had multiple problems with mplayer and mplayerplug-in in dapper.
I have got quite much help from this forums, so I hope this helps.

---

### Post by Gremlinzzz on 2006-11-27
Don't know if this is the problem but after i install w32codecs i scanned with virus scanner and found The file //usr/lib/codecs/vp31vfw.dll is infected with the W32/Magistr.a@MM virus!this was fresh install and i scanned
 before adding codecs.that scan was clean.

---

### Post by Gremlinzzz on 2006-11-27
Got it working just followed Kubunteandos advice.just configured the plugin to x11.right click on plugin video choose x11 and click ok.thanks Kubunteando

---


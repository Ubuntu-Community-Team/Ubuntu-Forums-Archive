---
title: "[SOLVED] Installed Myth TV Web Interface, what's next?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by WebSiteGuru on 2007-09-05
OK! I had finally installed Myth TV web interface. What should I do to configure it? I dont see any GUI for it, so I can configure the setting for Myth TV.

Can someone enlight me on this please, thanks!

---

### Post by gautada on 2007-09-05
[MythWeb]("http://www.mythtv.org/wiki/index.php/MythWeb") which is the web interface via Apache.  If so you still need to configure Apache. Use the link for details.

---

### Post by WebSiteGuru on 2007-09-05
> **gautada said:**
> [MythWeb]("http://www.mythtv.org/wiki/index.php/MythWeb") which is the web interface via Apache.  If so you still need to configure Apache. Use the link for details.

Uhh! Sound like I had installed the wrong MythTV. I need the one that I can use to view Video on the web. I am not trying to build a website with streaming video (at least not yet anyway).

I was told that some use MythTV to view video through the web and I can get better control on the setting.

So, where can I find that part of the software? Sympatic? (There are too many of thme in sympatic when I search for it).:confused:

---

### Post by ericmitz on 2007-09-05
MythWeb is mostly used for schedual management...

It does have a "recorded programs" section, from which you can download your recorded shows via the net, but this is usually not very pratcicle if you only have like comcast broadband or something, the upload speeds just arnt fast enough to download 2GB+ mpegs.

if you type [http://localhost/mythweb](http://localhost/mythweb) into firefox, does the MythWeb interface come up?

---

### Post by por100pre1 on 2007-09-05
> **ericmitz said:**
> MythWeb is mostly used for schedual management...

It does have a "recorded programs" section, from which you can download your recorded shows via the net, but this is usually not very pratcicle if you only have like comcast broadband or something, the upload speeds just arnt fast enough to download 2GB+ mpegs.

if you type [http://localhoast/mythweb](http://localhoast/mythweb) into firefox, does the MythWeb interface come up?

Excuse me, isn't [http://localhost/mythweb](http://localhost/mythweb) the page? :confused:

---

### Post by ericmitz on 2007-09-05
> **por100pre1 said:**
> Excuse me, isn't [http://localhost/mythweb](http://localhost/mythweb) the page? :confused:


Yes, that was a typo. sorry

[http://localhost/mythweb](http://localhost/mythweb)

---

### Post by WebSiteGuru on 2007-09-05
> **ericmitz said:**
> MythWeb is mostly used for schedual management...

It does have a "recorded programs" section, from which you can download your recorded shows via the net, but this is usually not very pratcicle if you only have like comcast broadband or something, the upload speeds just arnt fast enough to download 2GB+ mpegs.

if you type [http://localhost/mythweb](http://localhost/mythweb) into firefox, does the MythWeb interface come up?

Let me get this straight, you are telling me that I can record video off the web with this, right?

Also, can I use MythWeb to watch video from the web? I am a little confused :confused: here. Still kind of new to all this stuffs. ;) (But willing to learn)

---

### Post by gautada on 2007-09-06
> Let me get this straight, you are telling me that I can record video off the web with this, right?

No you can get your recordings that were made by your MythTV to the web and you can schedule recording from this interface via the web.  It is just a control interface for your MythTV.

> can I use MythWeb to watch video from the web?

Yes as long as it was recorded/in you MythTV system.  Not random stuff from the web.

> Uhh! Sound like I had installed the wrong MythTV. I need the one that I can use to view Video on the web

You sound like you need MythBrowser (which is easily installed from synaptic).  Then you can setup your video streaming server separately and use myth as your client.  The settings for myth browser allow you to use an external browser like FireFox so you can easily get all the Codecs (MPEG) etc needed for playback.

---

### Post by WebSiteGuru on 2007-09-06
> **gautada said:**
> No you can get your recordings that were made by your MythTV to the web and you can schedule recording from this interface via the web.  It is just a control interface for your MythTV.

Oh, OKKIE!

> **gautada said:**
> Yes as long as it was recorded/in you MythTV system.  Not random stuff from the web.

What do you mean by random?

> **gautada said:**
> You sound like you need MythBrowser (which is easily installed from synaptic).  Then you can setup your video streaming server separately and use myth as your client.  The settings for myth browser allow you to use an external browser like FireFox so you can easily get all the Codecs (MPEG) etc needed for playback.

That's it! MythBrowser was what I should have installed, I'll try that tonight (if I dont get side track again). :D

---

### Post by gautada on 2007-09-10
> **WebSiteGuru said:**
> What do you mean by random?

I mean video like from YouTube, since there are thousands of sites, etc...  I used random as you did not specify the video source.

---

### Post by WebSiteGuru on 2007-09-10
Nevermind, I had removed it. It cause my VLC not to show video at all on a paid subscription site. I am now trying to fix that problem :(

---


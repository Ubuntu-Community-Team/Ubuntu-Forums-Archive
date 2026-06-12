---
title: "What is wrong with the package &quot;mozilla-mplayer&quot;?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-11-04
Hello!

I used to be able to play Quicktime videos with the package "mozilla-mplayer" in Ubuntu v6.10 - Dapper Drake.

And specifically, I used to be able to play the following video at the site:

> [http://www.pixar.com/featurefilms/ts/theater/index.html](http://www.pixar.com/featurefilms/ts/theater/index.html)

Teaser Trailer
240x180

But, now that I have installed the package "mozilla-mplayer" & I click on the site's "240x180" resolution choice, I get the following error:

> Totem could not play 'fd://0'.
You do not have a decoder installed to handle this file.
You might need to install the necessary plugins.

What do I do?

Under Dapper Drake, no additional packages were required in order to play quicktime videos...

What package do I have to install?

OR

Is there some other program I could direct Quicktime videos to be played with, instead of Totem, and how would I do this?

Thanks.

P.S.> Please do not suggest me to install package "automatix"

---

### Post by llamakc on 2006-11-04
sudo apt-get remove  totem-gstreamer-firefox-plugin
 sudo apt-get install --reinstall mozilla-mplayer 




Fixed it for me.

---

### Post by Shay Stephens on 2006-11-04
A second way to get it working, I installed it via automatix and it worked for me.  I have not tried the uninstall of the gstreamer plugin, but next time I will try that.

---

### Post by dvarsam on 2006-11-04
> **llamakc said:**
> 
sudo apt-get remove  totem-gstreamer-firefox-plugin
sudo apt-get install --reinstall mozilla-mplayer 

Fixed it for me.

I searched in Synaptic for:

> 1. totem-gstreamer-firefox-plugin

2. totem-xine-firefox-plugin

3. frostwire

And all of the above packages do not exist!!!

What lines am I missing from "sources.list" to be able to install these packages?

Thanks.

---

### Post by llamakc on 2006-11-04
mozilla-mplayer is in multiverse, and the totem-* package appears to be called totem-mozilla:

```

apt-cache show totem-mozilla
Package: totem-mozilla
Priority: optional
Section: web
Installed-Size: 60
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: all
Source: totem
Version: 2.16.2-0ubuntu1
Replaces: totem-gstreamer-firefox-plugin, totem-xine-firefox-plugin
Provides: totem-gstreamer-firefox-plugin, totem-xine-firefox-plugin

```


So remove totem-mozilla and reinstall mozilla-mplayer should be the trick now.

---

### Post by dvarsam on 2006-11-05
> **llamakc said:**
> 
mozilla-mplayer is in multiverse.

The totem-* package appears to be called totem-mozilla:

So remove totem-mozilla and reinstall mozilla-mplayer should be the trick now.

Dear "llamakc",

Thanks for your reply!

Without you, I would be still wondering...

If I combine your last message with your previous one, then I should get the following:

Since package "totem" is now called "totem-mozilla",

then instead of typing:

> sudo apt-get remove totem-gstreamer-firefox-plugin

as you suggested before, I should now type:

> sudo apt-get remove totem-mozilla-gstreamer-firefox-plugin

And then type the command you suggested:

> sudo apt-get install --reinstall mozilla-mplayer

One thing I can NOT understand is this:

> What is the difference between the packages:

1. totem

2. totem-mozilla

3. totem-gstreamer-firefox-plugin

4. totem-mozilla-gstreamer-firefox-plugin

Cause all of them are SOOOOO mixed up, dude!!!

At the same time, can somebody tell me what line am I missing in my "sources.list" file to be able to locate with Synaptic the following packages:

1. totem-gstreamer-firefox-plugin

2. totem-xine-firefox-plugin

3. frostwire

Finally, providing to me the following answer:

> For the rest, please look in "multiverse", or "singleverse", or "universe", or "plentyverse",

Does NOT really help me at all...

What I would really like is the full line, I am missing...

Thanks.

---

### Post by aysiu on 2006-11-05
How about this? ```
cd /usr/lib/firefox/plugins
sudo rm totem*
```

---

### Post by Shay Stephens on 2006-11-05
> **aysiu said:**
> How about this? ```
cd /usr/lib/firefox/plugins
sudo rm totem*
```
Ahhh beautiful simplicity :D

---

### Post by NoJock on 2006-12-29
Thanks great job, Im new to linux only been playing with for 6 or so mnths and now getting around to playing some more. Have several differant install 4 linux and winxp all on one drive so i have to be real carful not to blow it up. Thanks agin it works well!

---

